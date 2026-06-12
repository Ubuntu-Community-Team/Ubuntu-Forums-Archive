---
title: "problem with env vars please help"
date: 2008-06-29
forum: General Help
---

### Post by chemicalgr on 2008-06-29
hello
i'm trying to use a bundle of tomcat-liferay,but i cannot setup the evn vars ...i've followed the procedure from threads of this forum but i have not succeed.

1.I'm using Sun's jre and jdk (i would like to)

```
chemical@chemical:/usr/local/liferay-portal-tomcat-5.5-jdk5-4.4.2/bin$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/jdk1.6.0/jre/bin/java
          2    /usr/bin/cacao
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/bin/gij-4.2
 +        5    /usr/lib/jvm/java-gcj/jre/bin/java
          6    /usr/bin/gij-4.1


```

2. above the configed .bashrc file in my home dir

```
# set the JAVA_HOME and JDK_HOME above
   export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/bin
   export  JRE_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin
```

3.when i run the startup.sh in the bundle's folder 
```
chemical@chemical:/usr/local/liferay-portal-tomcat-5.5-jdk5-4.4.2/bin$ ls
bootstrap.jar                  cpappend.bat           lportal.properties  setenv.sh     tomcat5w.exe          version.sh
catalina.bat                   digest.bat             lportal.script      shutdown.bat  tomcat-juli.jar
catalina.sh                    digest.sh              service.bat         shutdown.sh   tomcat-native.tar.gz
catalina-tasks.xml             jkstatus-tasks.xml     setclasspath.bat    startup.bat   tool-wrapper.bat
commons-daemon.jar             jmxaccessor-tasks.xml  setclasspath.sh     startup.sh    tool-wrapper.sh
commons-logging-api-1.1.1.jar  jsvc.tar.gz            setenv.bat          tomcat5.exe   version.bat
chemical@chemical:/usr/local/liferay-portal-tomcat-5.5-jdk5-4.4.2/bin$ sudo ./startup.sh
[B]Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program[/B]

```

Please help me out to make this work!!

thanks

---

### Post by jamesstansell on 2008-06-29
Does this thread help?

[http://ubuntuforums.org/showpost.php?p=5151783&postcount=11](http://ubuntuforums.org/showpost.php?p=5151783&postcount=11)

---

