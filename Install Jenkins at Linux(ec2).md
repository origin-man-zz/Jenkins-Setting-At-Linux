# Jenkins 설치
## Java8 설치
* AWS Linux 에 기본으로 설치된 자바버전은 7 이다. Jenkins 는 Java 8 이 필요하므로 기존 java 는 지우고 java 8 을 재설치 하도록 한다.
~~~
$ sudo yum remove java-1.7.0-openjdk
$ sudoyum install java-1.8.0
~~~  

*  yum 이 어디서 jenkins 를 설치해야 할지 알 수 있도록 Jenkins repository 를 추가해준다.
~~~
$ sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
~~~  

* Jenkins 를 설치할 때, 파일들이 신뢰할 수 있는 source 로 부터 제공됨을 증명하기 위해 로컬 GPG 키링에 Jenkins GPG key 를 추가해준다.
~~~
$ sudo rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
~~~  

* Jenkins 설치
~~~
$ sudo yum install jenkins
~~~  

* Jenkins 서버 시작
~~~
$ sudo service jenkins start
~~~  

* 8080 port LISTEN 하고 있는지 확인
~~~
$ netstat -na | grep 8080
~~~  

## Jenkins 서버 접속 & 초기 설정

* 이제 http://${your-ec2-public-dns}:8080 으로 접속하면 아래와 같은 화면이 뜰 것이다.
![Alt text](/img.jpg)

* 초기 접속 비밀번호는 /var/lib/jenkins/secrets/initialAdminPassword 여기에 있다는 말이다.
~~~
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
~~~
실행 후 나온 스트링을 복붙한다

* 다음화면에서 플러그인을 필요한 것만 설치할지, 디폴트로 설치할지 선택한다. 일단은 suggested plugins 을 다 설치하도록 한다.
![Alt text](/img.jpg)

* 추가로, 혹시 jenkins 서버에 git 이 설치되어있지 않다면 아래 명령어로 git 은 설치되어있는지 확인해주면 나중에 편하다.
~~~ 
$ yum install git
~~~

