---
title: "Maltigo Does not launch  ubuntu 18.04 LTS"
date: 2018-09-03
forum: General Help
---

### Post by masterx90 on 2018-09-03
Hello All,
I have installed Maltego from there official webiste, from 2 days I am trying find the solution, search all over internet. But, could not find the solution.
Maltigo, installed properly, but it does not launch.

However, I have tried running it from command line. it throws warnings...
```
java is /usr/bin/java
found java executable in PATH
pwd: file:/usr/share/maltego/maltego-ui/modules/ext/Java_Config_App.jar
install conf: /usr/share/maltego/etc/maltego.conf
install version: v4.1.13
user conf: /home/machinex90/.maltego/v4.1.13/etc/maltego.conf
current java: /usr/lib/jvm/java-11-openjdk-amd64
/usr/lib/jvm: /usr/lib/jvm
/usr/lib/jvm: /usr/lib/jvm/java-1.11.0-openjdk-amd64
/usr/lib/jvm: /usr/lib/jvm/java-11-openjdk-amd64
does not exist: /usr/lib/jvm/bin/java
not jre/jdk: /usr/lib/jvm
/usr/lib/jvm/java-1.11.0-openjdk-amd64 VS /usr/lib/jvm/java-11-openjdk-amd64 (/usr/lib/jvm/java-11-openjdk-amd64/bin/java)
/usr/lib/jvm/java-1.11.0-openjdk-amd64 sym /usr/lib/jvm/java-11-openjdk-amd64
trying path: /usr/lib/jvm/java-1.11.0-openjdk-amd64
canonical: /usr/lib/jvm/java-11-openjdk-amd64
javaHome: /usr/lib/jvm/java-1.11.0-openjdk-amd64
resource:com/paterva/maltego/java/config/jre/TestJDK.class -> /tmp/temp1107483000092884722097531786175544/TestJDK.class
executing: /usr/lib/jvm/java-11-openjdk-amd64/bin/java -classpath /tmp/temp1107483000092884722097531786175544 TestJDK, in: .
 result: 0
 command execution finished
 out: 10.0.2, 10.0.2+13-Ubuntu-1ubuntu0.18.04.1, Oracle Corporation, Linux, amd64
runtimes: 0
Warning: Could not find a suitable Java runtime.
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.netbeans.ProxyURLStreamHandlerFactory (file:/usr/share/maltego/platform/lib/boot.jar) to field java.net.URL.handler
WARNING: Please consider reporting this to the maintainers of org.netbeans.ProxyURLStreamHandlerFactory
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release]
```

I have maltego with others Destops like, Mint, Manjaro no issues..

Please help me finding the solution.

Thank you.

---

