---
title: "Java plugins stopped working in browser"
date: 2013-03-31
forum: General Help
---

### Post by MAFoElffen on 2013-03-31
OK... sort of at a loss. Java "was" working great, until today? as far as I know, it's working, but not on FireFox nor Chrome. Both say they "Cannot load Java(TM) Plugin 1.7.15."

I have OpenJavaJDK's 6 and 7 (default). Oracle JDK and JRE version 7... NetBeans and Eclispe JEE. I've been converting and revamping some server Management Utiltiies for my servers, which some are Java app's and Java Web app's. 

So locally everything seems to be fine. Browser are now boinked for "some" reason.
```

mafoelffen@maferr-ubuntu-1:~$ java -version
java version "1.7.0_17"
Java(TM) SE Runtime Environment (build 1.7.0_17-b02)
Java HotSpot(TM) 64-Bit Server VM (build 23.7-b01, mixed mode)

```
```

mafoelffen@maferr-ubuntu-1:~$ dpkg -l | grep -i openjdk
ii  icedtea-7-jre-jamvm:amd64              7u15-2.3.7-0ubuntu1~12.10.1               amd64        Alternative JVM for OpenJDK, using JamVM
ii  icedtea-7-plugin:amd64                    1.3-1ubuntu1.1                                   amd64        web browser plugin based on OpenJDK and IcedTea to execute Java applets
rc  openjdk-6-jre-headless:amd64          6b27-1.12.3-0ubuntu1~12.10                amd64        OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jdk:amd64                       7u15-2.3.7-0ubuntu1~12.10.1               amd64        OpenJDK Development Kit (JDK)
ii  openjdk-7-jre:amd64                       7u15-2.3.7-0ubuntu1~12.10.1               amd64        OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:amd64          7u15-2.3.7-0ubuntu1~12.10.1               amd64        OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                             7u15-2.3.7-0ubuntu1~12.10.1               all          OpenJDK Java runtime (architecture independent libraries)

```
And 
```

mafoelffen@maferr-ubuntu-1:~$ echo "JAVA_HOME: $JAVA_HOME" && ls -l $JAVA_HOME/jre/lib/amd64/libnpjp2.so && ls -l ~/.mozilla/plugins/
JAVA_HOME: /usr/lib/jvm/jdk1.7.0
-rwxr-xr-x 1 mafoelffen mafoelffen 203560 Feb 15 13:19 /usr/lib/jvm/jdk1.7.0/jre/lib/amd64/libnpjp2.so
total 0
lrwxrwxrwx 1 mafoelffen mafoelffen 46 Feb 23 13:05 libnpjp2.so -> /usr/lib/jvm/jdk1.7.0/jre/lib/i386/libnpjp2.so

```



But I did upgrade Eclipse 2 days ago from the repo version 3.8 (removed through Software Center) to Juno, v 4.2 becuase the Anroid SDK wasn't working right with the older Eclipse version.
```

Start-Date: 2013-03-28  09:20:09
Commandline: aptdaemon role='role-remove-packages' sender=':1.76'
Remove: libtomcat7-java:amd64 (7.0.30-0ubuntu1.1), libdb5.1-java-gcj:amd64 (5.1.29-5ubuntu2), libcommons-pool-java:amd64 (1.5.6-1build1), libdb-je-java:amd64 (3.3.98-1), junit4:amd64 (4.10-3), libgeronimo-jta-1.1-spec-java:amd64 (1.1.1-2ubuntu2), libecj-java:amd64 (3.5.1-4), eclipse-jdt:amd64 (3.8.0~rc4-1ubuntu1), libdb5.1-java-jni:amd64 (5.1.29-5ubuntu2), eclipse-platform-data:amd64 (3.8.0~rc4-1ubuntu1), libxerces2-java:amd64 (2.11.0-6), libswt-gtk-3-jni:amd64 (3.8.0~rc4-1), libxz-java:amd64 (1.1-1), eclipse-pde:amd64 (3.8.0~rc4-1ubuntu1), libjtidy-java:amd64 (7+svn20110807-4), libicu4j-java:amd64 (4.2.1.1-1), eclipse-rcp:amd64 (3.8.0~rc4-1ubuntu1), libaspectj-java:amd64 (1.6.12+dfsg-3), libswt-cairo-gtk-3-jni:amd64 (3.8.0~rc4-1), libcommons-beanutils-java:amd64 (1.8.3-3), libjetty8-java:amd64 (8.1.3-4), libosgi-compendium-java:amd64 (4.3.0-1), junit:amd64 (3.8.2-8build1), libdb-java:amd64 (5.1.6), libgeronimo-jpa-2.0-spec-java:amd64 (1.1-2), libkxml2-java:amd64 (2.3.0+ds1-2), libcommons-cli-java:amd64 (1.2-3ubuntu1), libfelix-gogo-runtime-java:amd64 (0.10.0-1), libcommons-logging-java:amd64 (1.1.1-9ubuntu1), libcommons-compress-java:amd64 (1.4.1-2ubuntu1), libfelix-gogo-shell-java:amd64 (0.10.0-1), libswt-gtk-3-java:amd64 (3.8.0~rc4-1), libdb5.1-java:amd64 (5.1.29-5ubuntu2), libicu4j-4.4-java:amd64 (4.4.2.2-1), libswt-gnome-gtk-3-jni:amd64 (3.8.0~rc4-1), libosgi-foundation-ee-java:amd64 (4.2.0-1), ant:amd64 (1.8.2-4build2), libservlet3.0-java:amd64 (7.0.30-0ubuntu1.1), default-jdk:amd64 (1.7-43ubuntu3), aspectj:amd64 (1.6.12+dfsg-3), libjsch-java:amd64 (0.1.48-0ubuntu1), libeasymock-java:amd64 (2.4+ds1-7), jarwrapper:amd64 (0.43ubuntu2), libxml-commons-resolver1.1-java:amd64 (1.2-7build1), ant-optional:amd64 (1.8.2-4build2), libapache-pom-java:amd64 (10-2build1), libxml-commons-external-java:amd64 (1.4.01-2build1), libcommons-dbcp-java:amd64 (1.4-3ubuntu1), libosgi-core-java:amd64 (4.3.0-3), sat4j:amd64 (2.3.1-1ubuntu1), eclipse:amd64 (3.8.0~rc4-1ubuntu1), libservlet2.5-java:amd64 (6.0.35-5), libcommons-httpclient-java:amd64 (3.1-10build1), libasm3-java:amd64 (3.3.2-1build1), libregexp-java:amd64 (1.5-3build1), libfelix-gogo-command-java:amd64 (0.12.0-2), fastjar:amd64 (0.98-4), libcommons-codec-java:amd64 (1.6-1), libcommons-lang-java:amd64 (2.6-3ubuntu2), libhamcrest-java:amd64 (1.2-2build1), liblucene2-java:amd64 (2.9.4+ds1-4), libfelix-osgi-obr-java:amd64 (1.0.2-3fakesync1), libgeronimo-osgi-support-java:amd64 (1.0-2), libequinox-osgi-java:amd64 (3.8.0~rc4-1ubuntu1), libcommons-parent-java:amd64 (22-2build1), libcommons-collections3-java:amd64 (3.2.1-5build1), eclipse-platform:amd64 (3.8.0~rc4-1ubuntu1), libfelix-bundlerepository-java:amd64 (1.6.6-1), libcommons-digester-java:amd64 (1.8.1-3), libjline-java:amd64 (1.0-2), libswt-webkit-gtk-3-jni:amd64 (3.8.0~rc4-1), libswt-glx-gtk-3-jni:amd64 (3.8.0~rc4-1)
End-Date: 2013-03-28  09:21:10

```
Anyone with ideas on getting the Browser plugins working again?

---

### Post by ManamiVixen on 2013-04-01
I  think I read somewhere that Firefox will not use the OpenJDK plugin anymore due to security reasons. I could be wrong on that. You might need the official Java now.

---

### Post by MAFoElffen on 2013-04-01
Look back at post 1. It is using the Oracle jdk and jre alongside the OpenJDK. installed the Java JDK as an Ubuntu alternatives mechanism (update-java-alternatives)... If you don't know what that means, google it. All worked until earlier today. Still works locally... Except for now, the true Java browser plugins. Which I notice the plugins are 1.7_15 and my Java Version is 1.7_17...

As for OPenJDK being unsecured. Well, Oracle Java 7 is noted as compromised also, and I do now get popups saying that I am using an us-secured version of Java and is asking me if I want to update... Hmmm. Maybe something is locking that down now? It still has protection displaying what is asking java to run and from what... But I did hit the Update button on one of those popup's and "then" it stopped working. Everything in the browser's say the plugin's are still enabled.

Maybe I should bring up my java console page or one of my own own written javascript browser "game extensions" and trace it. It would not be as frustrating if it was completely broke and not working at all. If you know anything about the SDK 7 Java Control Panel, I allow browsers to execute Java app's, but security level is set to "high" with trusted java certs. Prompts if not matching. My local network momitoring app's are https/ssl with local certs.

But when a browser page loads and says at load start "Cannot load **Java(TM)** Plugin..." That is the Oracle pluggin and for some reason there but "not" loading.

You know. If I don't find an answer in the next few days, well... There's always uninstall my JDK's and and re-install it. Just hours of time right?

---

### Post by MAFoElffen on 2013-04-01
ManamiVixen-

You were sort of on the right track, which led me to the answer. OpenJDK and the browsers had updates concerning Java Security. I had the browsers set manually to use the Oracle JRE instead of through update alternatives. I had the 1.7.0 SDK installed. When it updated the browser plugin, it assumed that the /etc/lib/jvm java base directory was jre1.7.0 instead of jdk1.7.0... so it then broke all the java symlinks. In the meantime, OpenJDK had an update and somehow reset the default update-alternatives back to it. This time instead of doing the jdk as update alternatives and the jre as manual (manually creating the individual symlinks)-- Understanding update-alternatives in Ubuntu a little better now, this time I set everything up generically through update-alternatives.

Long story short- Instead of fixing the now outdated JDK 1.7.0, I installed installed the newer JDK 1.7.0_17, which has all the newest security updates... I came up with a script to work it all out for me and to help me redo my servers and other dev test boxes here.

```

#!/bin/sh


## Script to add oracle JDK 1.7.0_17 as update-alternate
## Name: update-javasdk-update-alternatives.sh
# -- MAFoElffen <mafoelffen@ubuntu.com> 2013.4.1
#
# Clean this up


## This was for "Broken" JDK
# echo "JAVA_HOME: $JAVA_HOME"            |--| JAVA_HOME: /usr/lib/jvm/jdk1.7.0
#
# changed in ~/.bashrc to /usr/lib/jvm/default-java, so that update-alternatives can take care of it...
# Related in .bashrc is now:
# - export JAVA_HOME=/usr/lib/jvm/default-java
# - export JDK_HOME=/usr/lib/jvm/default-java
# - export MOZILLA_HOME=~/.mozilla
# - export PATH=/home/mafoelffen/adroid-sdks/eclipse:$PATH
# - export PATH=/opt/eclipse:$PATH


## This was for chrome
# ls $JAVA_HOME/jre/lib/amd64/libnpjp2.so |--| /usr/lib/jvm/jdk1.7.0/jre/lib/amd64/libnpjp2.so
#
# Make as symlink through "default-java" directory to work with update alts.


## This was for mozilla
# ls ~/.mozilla/plugins/                  |--| libnpjp2.so -> /usr/lib/jvm/jdk1.7.0/jre/lib/i386/libnpjp2.so
# 
# Removed symlink to let overall sys take care of it, instead of by user. That way it's changed by update alts.
rm ~/.mozilla/plugins/libnpjp2.so


# 32 bit version
if [ -f /usr/lib/jvm/jdk1.7.0_17/jre/lib/i386/libnpjp2.so ]; then
  # Install symlinks as update-alternatives
  sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0_17/bin/java" 1
  sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0_17/bin/javac" 1
  sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jdk1.7.0_17/jre/lib/i386/libnpjp2.so" 1
  sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0_17/bin/javaws" 1


# Then pick the update-alternatives
# I'm doing this in manaul mode to select which...
  sudo update-alternatives --config java
  sudo update-alternatives --config javac
  sudo update-alternatives --config mozilla-javaplugin.so
  sudo update-alternatives --config javaws
  exit 0


# 
elif [ -f /usr/lib/jvm/jdk1.7.0_17/jre/lib/amd64/libnpjp2.so ]; then 
  # Install symlinks as update-alternatives
  sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0_17/bin/java" 1
  sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0_17/bin/javac" 1
  sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jdk1.7.0_17/jre/lib/amd64/libnpjp2.so" 1
  sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0_17/bin/javaws" 1


# Then pick the update-alternatives
# I'm doing this in manaul mode to select which...
  sudo update-alternatives --config java
  sudo update-alternatives --config javac
  sudo update-alternatives --config mozilla-javaplugin.so
  sudo update-alternatives --config javaws
  exit 0


# 
else 
  echo "Not installed. Nothing to do."
  exit 1
fi


# update-alternatives does not update the symlink /usr/lib/jvm/default-java
# to the new java directory.
# This did not want to update via a script, so changed it myself manually

```
Then then search for other java symlinks and found ~/home/libnpjp2.so which still pointed to the old jdk1.7.0... but since everything is now working fine now, I deleted it.

---

