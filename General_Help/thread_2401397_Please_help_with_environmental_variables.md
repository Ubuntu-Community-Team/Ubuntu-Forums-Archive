---
title: "Please help with environmental variables?"
date: 2018-09-17
forum: General Help
---

### Post by marika.alicja on 2018-09-17
Hi,

I have two sets of JDK + Maven, which I need to switch between:

/usr/lib/jvm/jdk1.6.0_45/
/opt/apache-maven-3.2.5

/usr/lib/jvm/jdk1.8.0_181/
/opt/apache-maven-3.5.4

Currently I want the latter. Somehow I can't set the environmental variables properly, I keep getting:

```
marika:~ $ java -version
Command 'java' not found, but can be installed with..

marika:/opt/apache-maven-3.2.5 $ echo $JAVA_HOME
/usr/lib/jvm/jdk1.8.0_181/

marika:~ $ mvn -v
The JAVA_HOME environment variable is not defined correctly
This environment variable is needed to run this program
NB: JAVA_HOME should point to a JDK not a JRE

marika:/opt/apache-maven-3.2.5 $ echo $MAVEN_HOME
/opt/apache-maven-3.5.4/
```

My config:

**/etc/environents**

JAVA_HOME="/usr/lib/jvm/jdk1.8.0_181/"
MAVEN_HOME="/opt/apache-maven-3.5.4/"
CATALINA_HOME="/opt/apache-tomcat-6.0.26/"

# JAVA_HOME="/usr/lib/jvm/jdk1.6.0_45/"
# MAVEN_HOME="/opt/apache-maven-3.2.5/"
# CATALINA_HOME="/opt//apache-tomcat-6.0.26/"

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/lib/jvm/jdk1.8.0_181/bin:/opt/apache-maven-3.5.4/bin:/opt/apache-tomcat-6.0.26/"


**~/.bashrc**

...

export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_181
export MAVEN_HOME=/opt/apache-maven-3.5.4
export CATALINA_HOME=/opt/apache-tomcat-6.0.26

# export JAVA_HOME=/usr/lib/jvm/jdk1.6.0_45
# export MAVEN_HOME=/opt/apache-maven-3.2.5
# export CATALINA_HOME=/opt/apache-tomcat-6.0.26

export PATH=${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${CATALINA_HOME}/bin:${PATH}


**/etc/profile.d/maven.sh** 

export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_181
export MAVEN_HOME=/opt/apache-maven-3.5.4
export PATH=${JAVA_HOME}/bin:${PATH}

# export JAVA_HOME=/usr/lib/jvm/jdk1.6.0_45
# export MAVEN_HOME=/opt/apache-maven-3.2.5
# export PATH=${JAVA_HOME}/bin:${PATH}

Probably all this duplication of adding to PATH is a mistake, but I just didn't know what to do anymore. Can you please point me in the right direction?

---

### Post by TheFu on 2018-09-18
I don't use JAVA or Maven.

Store the original path in a different read-only environment variable and use that to build the new PATH whenever you need to change between different tools.

I wouldn't touch  /etc/environments or  /etc/profile.d/maven.sh unless their instructions specifically say that is needed.  I would have an application startup script (or 2) that sets all the environments exactly as needed, then starts whatever daemons are needed.

I thought java had a way to switch between different environments?  Something about alternates ...

---

