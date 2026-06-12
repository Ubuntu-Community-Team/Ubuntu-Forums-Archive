---
title: "new jar issue"
date: 2019-04-29
forum: General Help
---

### Post by cmcanulty on 2019-04-29
As of a few days ago I can't run jar files anymore. I have googled a lot and tried various things with no luck. I have both open JDK java 8 runtime and oracle java 11 runtime. I tried to get a screenshot of the error boxes but they disappear as soon as I try a screenshot but the errors refer to java lang and javax swing fframe  get peer with java 8 and with java 11 java lang and javax swing fframe  get peer. I tried to find those packages but no luck. Jars ran fine until a few days ago. I do have the files marked executable. This is is the jin chess program.

[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=2ahUKEwiI1eaAoPbhAhUkgK0KHUuFBCsQFjAAegQILRAC&url=https%3A%2F%2Fwww.jinchess.com%2F&usg=AOvVaw0rdzhLAP4JkztAJ4JU_1kC]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=2ahUKEwiI1eaAoPbhAhUkgK0KHUuFBCsQFjAAegQILRAC&url=https%3A%2F%2Fwww.jinchess.com%2F&usg=AOvVaw0rdzhLAP4JkztAJ4JU_1kC")

---

### Post by Holger_Gehrke on 2019-04-29
java.lang and javax.swing are both part of the run time. It's **very** unlikely that they are missing - you'd have a severely broken java installation if they were. Probably the error message contained some kind of function call stack dump (problem happened in function a which was called by function b  which was called by function c ....). You could try to run the jar from the command line (cd to the directory where you put the jar, then run 'java -jar jin.jar'). Even if it doesn't work, it should put the error message in the terminal from where you could cut and paste it to this forum.

Holger

---

### Post by cmcanulty on 2019-04-30
Wowee that fixed it, now as a follow up how could I put that into a launcher? I tried and didn't work: 

```
thunar  /home/cmcanulty/jin-2.14.1/java -jar jin.jar
```

I also tried 

```
"thunar  /home/cmcanulty/jin-2.14.1/java -jar jin.jar"
```

Oh I got it OK after I ran your command the menu icon started working, 

thank you very much

---

### Post by Holger_Gehrke on 2019-04-30
There should be an executable bash-script named 'jin' in the directory with the jar. Set this script as the command to execute and the directory it's in as the working directory. I think there's even an image-file in that directory that can be used as an icon for the launcher ...

Holger

---

### Post by cmcanulty on 2019-04-30
I thought it was fixed but was wrong. Here is the terminal error
```

cmcanulty@hpomni:~$ sudo apt install oracle-java11-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java libatk-wrapper-java libatk-wrapper-java-jni
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  visualvm ttf-baekmuk | ttf-unfonts | ttf-unfonts-core ttf-kochi-gothic
  | ttf-sazanami-gothic ttf-kochi-mincho | ttf-sazanami-mincho
  ttf-arphic-uming
Recommended packages:
  oracle-java11-set-default
The following packages will be REMOVED:
  openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre
  openjdk-11-jre-headless
The following NEW packages will be installed:
  oracle-java11-installer
0 upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 35.1 kB of archives.
After this operation, 373 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic/main amd64 oracle-java11-installer amd64 11.0.2-2~linuxuprising1 [35.1 kB]
Fetched 35.1 kB in 15s (2,289 B/s)                 
Preconfiguring packages ...
(Reading database ... 345112 files and directories currently installed.)
Removing openjdk-11-jdk:amd64 (11.0.2+9-3ubuntu1~18.04.3) ...
Removing openjdk-11-jre:amd64 (11.0.2+9-3ubuntu1~18.04.3) ...
dpkg: openjdk-11-jre-headless:amd64: dependency problems, but removing anyway as you requested:
 default-jre-headless depends on openjdk-11-jre-headless.
 openjdk-11-jdk-headless:amd64 depends on openjdk-11-jre-headless (= 11.0.2+9-3ubuntu1~18.04.3).

Removing openjdk-11-jre-headless:amd64 (11.0.2+9-3ubuntu1~18.04.3) ...
Selecting previously unselected package oracle-java11-installer.
(Reading database ... 344787 files and directories currently installed.)
Preparing to unpack .../oracle-java11-installer_11.0.2-2~linuxuprising1_amd64.deb ...
oracle-license-v1-2 license has already been accepted
Unpacking oracle-java11-installer (11.0.2-2~linuxuprising1) ...
dpkg: openjdk-11-jdk-headless:amd64: dependency problems, but removing anyway as you requested:
 default-jdk-headless depends on openjdk-11-jdk-headless; however:
  Package openjdk-11-jdk-headless:amd64 is to be removed.
  Package oracle-java11-installer which provides openjdk-11-jdk-headless is not configured yet.

(Reading database ... 344810 files and directories currently installed.)
Removing openjdk-11-jdk-headless:amd64 (11.0.2+9-3ubuntu1~18.04.3) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Setting up oracle-java11-installer (11.0.2-2~linuxuprising1) ...
No /var/cache/oracle-jdk11-installer/wgetrc file found.
Creating /var/cache/oracle-jdk11-installer/wgetrc and
using default oracle-java11-installer wgetrc settings for it.
Downloading Oracle Java 11...
--2019-04-30 15:16:23--  http://download.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.45.132.164
Connecting to download.oracle.com (download.oracle.com)|23.45.132.164|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz [following]
--2019-04-30 15:16:38--  https://edelivery.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.107.102.25, 2600:1407:a000:3b3::366, 2600:1407:a000:3a3::366
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.107.102.25|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz?AuthParam=1556651918_61820d7d82478e5ee224a5994af45281 [following]
--2019-04-30 15:16:38--  http://download.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz?AuthParam=1556651918_61820d7d82478e5ee224a5994af45281
Connecting to download.oracle.com (download.oracle.com)|23.45.132.164|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://download.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz?AuthParam=1556651918_61820d7d82478e5ee224a5994af45281 [following]
--2019-04-30 15:16:38--  https://download.oracle.com/otn-pub/java/jdk/11.0.2+9/f51449fcd52f4d52b93a989c5c56ed3c/jdk-11.0.2_linux-x64_bin.tar.gz?AuthParam=1556651918_61820d7d82478e5ee224a5994af45281
Connecting to download.oracle.com (download.oracle.com)|23.45.132.164|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 179640645 (171M) [application/x-gzip]
Saving to: ‘jdk-11.0.2_linux-x64_bin.tar.gz’

     0K ........ ........ ........ ........ 18% 4.47M 31s
 32768K ........ ........ ........ ........ 37% 3.71M 26s
 65536K ........ ........ ........ ........ 56% 4.29M 18s
 98304K ........ ........ ........ ........ 74% 3.97M 11s
131072K ........ ........ ........ ........ 93% 3.81M 3s
163840K ........ ...                       100% 3.04M=43s

2019-04-30 15:17:22 (3.95 MB/s) - ‘jdk-11.0.2_linux-x64_bin.tar.gz’ saved [179640645/179640645]

Download done.
Removing outdated cached downloads...
update-binfmts: warning: current package is oracle-java12, but binary format already installed by openjdk-8
Oracle JDK 11 installed

#####Important########
To set Oracle jdk11 as default, install the "oracle-java11-set-default" package.
E.g.: sudo apt install oracle-java11-set-default.
Processing triggers for shared-mime-info (1.9-2) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
cmcanulty@hpomni:~$ sudo apt install oracle-java11-set-default
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java libatk-wrapper-java libatk-wrapper-java-jni
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  oracle-java12-set-default
The following NEW packages will be installed:
  oracle-java11-set-default
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 3,116 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic/main amd64 oracle-java11-set-default amd64 11.0.2-2~linuxuprising1 [3,116 B]
Fetched 3,116 B in 15s (204 B/s)                     
(Reading database ... 344665 files and directories currently installed.)
Removing oracle-java12-set-default (12.0.1-1~linuxuprising1) ...
Selecting previously unselected package oracle-java11-set-default.
(Reading database ... 344663 files and directories currently installed.)
Preparing to unpack .../oracle-java11-set-default_11.0.2-2~linuxuprising1_amd64.deb ...
Unpacking oracle-java11-set-default (11.0.2-2~linuxuprising1) ...
Setting up oracle-java11-set-default (11.0.2-2~linuxuprising1) ...
Installing new version of config file /etc/profile.d/jdk.csh ...
Installing new version of config file /etc/profile.d/jdk.sh ...
cmcanulty@hpomni:~$ java -version
java version "11.0.2" 2019-01-15 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.2+9-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.2+9-LTS, mixed mode)
cmcanulty@hpomni:~$ 

```

 and
```

cmcanulty@hpomni:~/jin-2.14.1-unix$ java -jar jin.jar
java.lang.NoSuchMethodError: javax.swing.JFrame.getPeer()Ljava/awt/peer/ComponentPeer;
	at free.jin.ui.AbstractUiProvider.restoreFrameGeometry(Unknown Source)
	at free.jin.ui.MdiUiProvider.start(Unknown Source)
	at free.jin.Jin.start(Unknown Source)
	at free.jin.JinApplication.main(Unknown Source)
cmcanulty@hpomni:~/jin-2.14.1-unix$ java -jar jin.jar
```

---

### Post by Holger_Gehrke on 2019-04-30
Not loving Oracle Java, mainly because of their license. And with the recent change in their download policy version 11.0.2 is probably the last one you can get under package management because you need to have an account on oracle.com and be signed in to download newer versions ...

I'm using OpenJDK and have both versions 8 and 11 installed. My test yesterday was done using version 8. When I saw that you were using version 11, I switched to version 11 ('sudo update-java-alternatives --set java-1.11.0-openjdk-amd64') and got the same error you got. Switching back ('sudo update-java-alternatives --set java-1.8.0-openjdk-amd64') made it work again.So it seems like it's a matter of the version of Java you're using.

Oh, and the icon I mentioned in my last post is in the jin-directory and is named 'icon.png', appropriately enough ...

Holger

---

### Post by cmcanulty on 2019-05-01
I get the same errors

```
cmcanulty@hpomni:~$ sudo update-java-alternatives --set java-1.8.0-openjdk-amd64[sudo] password for cmcanulty: 
update-alternatives: error: no alternatives for jaccessinspector
update-alternatives: error: no alternatives for jaccesswalker
update-alternatives: error: no alternatives for kinit
update-alternatives: error: no alternatives for klist
update-alternatives: error: no alternatives for ktab
update-alternatives: error: no alternatives for mozilla-javaplugin.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
cmcanulty@hpomni:~$
``` 

```
cmcanulty@hpomni:~/jin-2.14.1-unix$ java -jar  jin.jar
java.lang.NoSuchMethodError: javax.swing.JFrame.getPeer()Ljava/awt/peer/ComponentPeer;
	at free.jin.ui.AbstractUiProvider.restoreFrameGeometry(Unknown Source)
	at free.jin.ui.MdiUiProvider.start(Unknown Source)
	at free.jin.Jin.start(Unknown Source)
	at free.jin.JinApplication.main(Unknown Source)
^Ccmcanulty@hpomni:~/jin-2.14.1-unix$ java -version
openjdk version "11.0.2" 2019-01-15
OpenJDK Runtime Environment (build 11.0.2+9-Ubuntu-3ubuntu118.04.3)
OpenJDK 64-Bit Server VM (build 11.0.2+9-Ubuntu-3ubuntu118.04.3, mixed mode, sharing)
cmcanulty@hpomni:~/jin-2.14.1-unix$ 

```


```

cmcanulty@hpomni:~$ java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
cmcanulty@hpomni:~$ 
```

I have installed installed openjdk Java 8 runtime and oracle java 12 runt```
cmcanulty@hpomni:~$ java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
cmcanulty@hpomni:~$ sudo update-java-alternatives 
[sudo] password for cmcanulty: 
usage: update-java-alternatives [--jre-headless] [--jre] [--plugin] [-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help
cmcanulty@hpomni:
```

I am SO frustrated wasting 2 days on this

---

