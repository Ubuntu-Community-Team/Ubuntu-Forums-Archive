---
title: "How to fix &quot;JAVA_HOME is set to an invalid directory&quot;"
date: 2018-11-02
forum: General Help
---

### Post by satimis on 2018-11-02
Hi all,

I was following below document to install Whatsapp on Ubuntu 18.04;
Run WhatsApp on Android SDK without a phone
[https://eureka.ykyuen.info/2012/02/05/run-whatsapp-on-android-sdk-without-a-phone/](https://eureka.ykyuen.info/2012/02/05/run-whatsapp-on-android-sdk-without-a-phone/)

Installation went throught without much problem.  On starting Avdmanger;

$ ./Android/Sdk/tools/bin/avdmanager ```


ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/java-7-oracle

Please set the JAVA_HOME variable in your environment to match the
location of your Java installation.

```

$ la -al /usr/lib/jvm/default-java```

lrwxrwxrwx 1 root root 25 Apr  8  2018 /usr/lib/jvm/default-java -> java-1.11.0-openjdk-amd64

```

$ la -al /usr/lib/jvm/```

total 28
drwxr-xr-x   5  668  668 4096 Nov  2 12:58 .
drwxr-xr-x 131 root root 4096 Nov  2 14:46 ..
lrwxrwxrwx   1 root root   25 Apr  8  2018 default-java -> java-1.11.0-openjdk-amd64
lrwxrwxrwx   1 root root   21 Oct  7 23:06 java-1.11.0-openjdk-amd64 -> java-11-openjdk-amd64
-rw-r--r--   1 root root 2619 Oct  7 23:06 .java-1.11.0-openjdk-amd64.jinfo
drwxr-xr-x   7 root root 4096 Nov  2 12:56 java-11-openjdk-amd64
lrwxrwxrwx   1 root root   20 Oct 23 01:29 java-1.8.0-openjdk-amd64 -> java-8-openjdk-amd64
-rw-r--r--   1 root root 2600 Oct 23 01:29 .java-1.8.0-openjdk-amd64.jinfo
drwxr-xr-x   5 root root 4096 Nov  2 12:58 java-8-openjdk-amd64
drwxr-xr-x   8  668  668 4096 Nov  1 23:26 jdk-11.0.1

```

$ ls /usr/lib/jvm/java-11-openjdk-amd64/```

bin  conf  docs  legal  lib  man

```

$ java --version```

openjdk 10.0.2 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.3)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.3, mixed mode)

```

Please advise how to fix the problem?  Thanks in advance

Regards
satimis

---

### Post by slickymaster on 2018-11-02
In a terminal window```
export JAVA_HOME=java_home_path # java_home_path being the folder where your bin/java is.
```

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> In a terminal window```
export JAVA_HOME=java_home_path # java_home_path being the folder where your bin/java is.
```
Hi,

Thanks for your advice.

$ sudo find / -name java | grep bin```

/home/satimis/Android/Sdk/sources/android-28/android/databinding/tool/reflection/java
/home/satimis/android-studio/jre/bin/java
/home/satimis/android-studio/jre/jre/bin/java
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
/usr/bin/java
/usr/lib/jvm/java-8-openjdk-amd64/bin/java
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
/usr/lib/jvm/java-11-openjdk-amd64/bin/java
/usr/lib/jvm/jdk-11.0.1/bin/java

```

**Which path shall I use;**
**[COLOR="#FF0000"]1.[/COLOR]**```

/home/satimis/android-studio/jre/bin/java

```

$ ls -al /home/satimis/android-studio/jre/bin/```

total 660
drwxrwxr-x 2 satimis satimis   4096 Oct  8 21:12 .
drwxrwxr-x 6 satimis satimis   4096 Oct  8 21:12 ..
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 appletviewer
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 extcheck
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 idlj
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jar
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jarsigner
-rwxr-xr-x 1 satimis satimis   8520 Oct  8 18:35 java
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 javac
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 javadoc
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 javah
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 javap
-rwxr-xr-x 1 satimis satimis   2806 Oct  8 18:35 java-rmi.cgi
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jcmd
-rwxr-xr-x 1 satimis satimis   8656 Oct  8 18:35 jconsole
-rwxr-xr-x 1 satimis satimis   8648 Oct  8 18:35 jdb
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jdeps
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jhat
-rwxr-xr-x 1 satimis satimis   8680 Oct  8 18:35 jinfo
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jjs
-rwxr-xr-x 1 satimis satimis   8680 Oct  8 18:35 jmap
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jps
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jrunscript
-rwxr-xr-x 1 satimis satimis   8648 Oct  8 18:35 jsadebugd
-rwxr-xr-x 1 satimis satimis   8680 Oct  8 18:35 jstack
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jstat
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jstatd
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 keytool
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 native2ascii
-rwxr-xr-x 1 satimis satimis   8688 Oct  8 18:35 orbd
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 pack200
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 policytool
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 rmic
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 rmid
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 rmiregistry
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 schemagen
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 serialver
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 servertool
-rwxr-xr-x 1 satimis satimis   8688 Oct  8 18:35 tnameserv
-rwxr-xr-x 1 satimis satimis 182336 Oct  8 18:35 unpack200
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 wsgen
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 wsimport
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 xjc

```

[B][COLOR="#FF0000"]
Or[/COLOR][/B]

**[COLOR="#FF0000"]2.[/COLOR]**```

/home/satimis/android-studio/jre/jre/bin/java

```

$ ls -al /home/satimis/android-studio/jre/jre/bin/```

total 308
drwxrwxr-x 2 satimis satimis   4096 Oct  8 21:12 .
drwxrwxr-x 4 satimis satimis   4096 Oct  8 21:12 ..
-rwxr-xr-x 1 satimis satimis   8520 Oct  8 18:35 java
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 jjs
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 keytool
-rwxr-xr-x 1 satimis satimis   8688 Oct  8 18:35 orbd
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 pack200
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 policytool
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 rmid
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 rmiregistry
-rwxr-xr-x 1 satimis satimis   8632 Oct  8 18:35 servertool
-rwxr-xr-x 1 satimis satimis   8688 Oct  8 18:35 tnameserv
-rwxr-xr-x 1 satimis satimis 182336 Oct  8 18:35 unpack200

```

**[COLOR="#FF0000"]Or[/COLOR]**

**[COLOR="#FF0000"]3.[/COLOR]**```

/usr/lib/jvm/java-11-openjdk-amd64/bin/java

```
 ls -al /usr/lib/jvm/java-11-openjdk-amd64/bin/```

total 224
drwxr-xr-x 2 root root   4096 Nov  2 12:56 .
drwxr-xr-x 7 root root   4096 Nov  2 12:56 ..
-rwxr-xr-x 1 root root  10344 Oct  7 23:06 java
-rwxr-xr-x 1 root root  10400 Oct  7 23:06 jjs
-rwxr-xr-x 1 root root  10376 Oct  7 23:06 keytool
-rwxr-xr-x 1 root root  10408 Oct  7 23:06 orbd
-rwxr-xr-x 1 root root  10376 Oct  7 23:06 pack200
-rwxr-xr-x 1 root root  10368 Oct  7 23:06 rmid
-rwxr-xr-x 1 root root  10376 Oct  7 23:06 rmiregistry
-rwxr-xr-x 1 root root  10376 Oct  7 23:06 servertool
-rwxr-xr-x 1 root root  10416 Oct  7 23:06 tnameserv
-rwxr-xr-x 1 root root 107456 Oct  7 23:06 unpack200

```

**[COLOR="#FF0000"]Or[/COLOR]**

**[COLOR="#FF0000"]4.[/COLOR]**```

/usr/lib/jvm/jdk-11.0.1/bin/java

```

$ ls -al /usr/lib/jvm/jdk-11.0.1/bin/```

total 516
drwxr-xr-x 2 668 668   4096 Nov  1 23:26 .
drwxr-xr-x 8 668 668   4096 Nov  1 23:26 ..
-rwxr-xr-x 1 668 668  12952 Oct  6 20:32 jaotc
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jar
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jarsigner
-rwxr-xr-x 1 668 668   8672 Oct  6 20:32 java
-rwxr-xr-x 1 668 668   8784 Oct  6 20:32 javac
-rwxr-xr-x 1 668 668   8784 Oct  6 20:32 javadoc
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 javap
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jcmd
-rwxr-xr-x 1 668 668  12888 Oct  6 20:32 jconsole
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jdb
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jdeprscan
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jdeps
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jhsdb
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jimage
-rwxr-xr-x 1 668 668  12880 Oct  6 20:32 jinfo
-rwxr-xr-x 1 668 668   8784 Oct  6 20:32 jjs
-rwxr-xr-x 1 668 668   8784 Oct  6 20:32 jlink
-rwxr-xr-x 1 668 668  12880 Oct  6 20:32 jmap
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jmod
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jps
-rwxr-xr-x 1 668 668   8792 Oct  6 20:32 jrunscript
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jshell
-rwxr-xr-x 1 668 668  12880 Oct  6 20:32 jstack
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jstat
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 jstatd
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 keytool
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 pack200
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 rmic
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 rmid
-rwxr-xr-x 1 668 668   8744 Oct  6 20:32 rmiregistry
-rwxr-xr-x 1 668 668   8736 Oct  6 20:32 serialver
-rwxr-xr-x 1 668 668 117656 Oct  6 20:32 unpack200

```

[B][COLOR="#FF0000"]
?[/COLOR][/B]

Thanks

Regards
satimis

---

### Post by slickymaster on 2018-11-02
Depending on what you intend to go, openjdk or pure jdk, use the the third option for the former or the forth for the later

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> Depending on what you intend to go, openjdk or pure jdk, use the the third option for the former or the forth for the later
How to revoke the command```

export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/bin/java

```
?

If unable to start Avdmanger for trying;```

export JAVA_HOME=/usr/lib/jvm/jdk-11.0.1/bin/java

```

Or just to re-run it ?

Thanks

satimis

---

### Post by slickymaster on 2018-11-02
You to remove **bin/java** from the end of the path while putting it into JAVA_HOME. Either```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
```or```
export JAVA_HOME=/usr/lib/jvm/jdk-11.0.1/
```

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> You to remove **bin/java** from the end of the path while putting it into JAVA_HOME. Either```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
```or```
export JAVA_HOME=/usr/lib/jvm/jdk-11.0.1/
```

It is very strange.  Non of them can work !

$ export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/java-11-openjdk-amd64/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```

$ export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
$ export JAVA_HOME=/usr/lib/jvm/jdk-11.0.1/bin/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/jdk-11.0.1/bin/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```


$ export JAVA_HOME=/usr/lib/jvm/jdk-11.0.1/
$ export JAVA_HOME=/home/satimis/android-studio/jre/bin/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /home/satimis/android-studio/jre/bin/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```


$ export JAVA_HOME=/home/satimis/android-studio/jre/
$ export JAVA_HOME=/home/satimis/android-studio/jre/jre/bin/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /home/satimis/android-studio/jre/jre/bin/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```


$ export JAVA_HOME=/home/satimis/android-studio/jre/jre/
$ export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/bin/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/java-8-openjdk-amd64/bin/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```


$ export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/
$ export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
$ ./Android/Sdk/tools/bin/avdmanager```


ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java

Please set the JAVA_HOME variable in your environment to match the location of your Java installation.

```

Do I need to reboot after running each command?

Regards
satimis

---

### Post by slickymaster on 2018-11-02
No, a reboot shouldn't be necessary. What do you get out of```
$JAVA_HOME/bin/java -version
```and also```
readlink -f $(which java)
```

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> No, a reboot shouldn't be necessary. What do you get out of```
$JAVA_HOME/bin/java -version
```and also```
readlink -f $(which java)
```


$ $JAVA_HOME/bin/java -version```

bash: /usr/lib/jvm/java-7-oracle/bin/java: No such file or directory

```

$ readlink -f $(which java)```

/usr/lib/jvm/java-11-openjdk-amd64/bin/java

```

satimis

---

### Post by slickymaster on 2018-11-02
Please execute once again ```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
``` without the end '/'
And what you get afterwards out of ```
$JAVA_HOME/bin/java -version
```

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> Please execute once again ```
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
``` without the end '/'
And what you get afterwards out of ```
$JAVA_HOME/bin/java -version
```
$ export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64

$ $JAVA_HOME/bin/java -version```

openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.3)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.3, mixed mode)

```

$ ./Android/Sdk/tools/bin/avdmanager```

Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.AvdManagerCli.run(AvdManagerCli.java:213)
        at com.android.sdklib.tool.AvdManagerCli.main(AvdManagerCli.java:200)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:583)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:190)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
        ... 5 more

```

satimis

---

### Post by slickymaster on 2018-11-02
Your JAVA_HOME issue is solved. You're facing now issues related to the software itself, so my advice would be to close this thread, marking it as solved and start a new one on this particular issue

---

### Post by satimis on 2018-11-02
> **slickymaster said:**
> Your JAVA_HOME issue is solved. You're facing now issues related to the software itself, so my advice would be to close this thread, marking it as solved and start a new one on this particular issue

Thanks

Regards
satimis

---

