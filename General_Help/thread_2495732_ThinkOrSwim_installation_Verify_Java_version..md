---
title: "ThinkOrSwim installation: Verify Java version."
date: 2024-02-28
forum: General Help
---

### Post by sks24 on 2024-02-28
Hi,
I'm having trouble making Zulu OpenJDK 11 the default Java version in my 22.04.3 LTS installation on my Lenovo M910Q Tiny. I think the problem might be that I accidentally installed zulu17-jdk. I tried to uninstall it, but it still shows as the default version upon executing the "java -version" command. I'm trying to follow the instructions shown [here]("https://docs.azul.com/core/install/debian") and [here]("https://www.tdameritrade.com/tools-and-platforms/thinkorswim/desktop/download.html"). Specifically at the latter URL: 
> thinkorswim requires Zulu OpenJDK 11 to run, general installation instructions can be found on the Zulu website.

Once Zulu OpenJDK 11 is installed, ensure it is set as the default Java VM using the steps specific to your Linux Distribution. After ensuring Zulu OpenJDK 11 is the default with the “java –version” command in a shell/terminal, continue with the installation instructions below:
Click "Install thinkorswim" to download the thinkorswim installer to a directory on your PC.
After downloading open a shell and CD to the directory where you downloaded the installer.
At the prompt type: sh ./thinkorswim_installer.sh

I recorded both attempts to install and set OpenJDK 11 as default. Here's the first: 
```



scott@scott-ThinkCentre-M910q:~$ sudo apt install gnupg ca-certificates curl
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ca-certificates is already the newest version (20230311ubuntu0.22.04.1).
ca-certificates set to manually installed.
gnupg is already the newest version (2.2.27-3ubuntu2.1).
gnupg set to manually installed.
The following additional packages will be installed:
  libcurl4
The following NEW packages will be installed:
  curl
The following packages will be upgraded:
  libcurl4
1 upgraded, 1 newly installed, 0 to remove and 191 not upgraded.
Need to get 194 kB/483 kB of archives.
After this operation, 454 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 curl amd64 7.81.0-1ubuntu1.15 [194 kB]
Fetched 194 kB in 0s (430 kB/s)
(Reading database ... 200080 files and directories currently installed.)
Preparing to unpack .../libcurl4_7.81.0-1ubuntu1.15_amd64.deb ...
Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.15) over (7.81.0-1ubuntu1.13) ...
Selecting previously unselected package curl.
Preparing to unpack .../curl_7.81.0-1ubuntu1.15_amd64.deb ...
Unpacking curl (7.81.0-1ubuntu1.15) ...
Setting up libcurl4:amd64 (7.81.0-1ubuntu1.15) ...
Setting up curl (7.81.0-1ubuntu1.15) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
scott@scott-ThinkCentre-M910q:~$ curl -s https://repos.azul.com/azul-repo.key | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg
scott@scott-ThinkCentre-M910q:~$ echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" | sudo tee /etc/apt/sources.list.d/zulu.list
deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main
scott@scott-ThinkCentre-M910q:~$ $ sudo apt update
$: command not found
scott@scott-ThinkCentre-M910q:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Get:4 https://dl.google.com/linux/chrome/deb stable InRelease [1,825 B]        
Get:5 https://repos.azul.com/zulu/deb stable InRelease [5,288 B]               
Hit:6 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Get:7 https://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,081 B]
Get:8 https://repos.azul.com/zulu/deb stable/main amd64 Packages [270 kB]
Fetched 278 kB in 1s (328 kB/s)   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
191 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://repos.azul.com/zulu/deb stable InRelease' doesn't support architecture 'i386'
scott@scott-ThinkCentre-M910q:~$ sudo apt install zulu<jdk-version>-jdk
bash: jdk-version: No such file or directory
scott@scott-ThinkCentre-M910q:~$ sudo apt install zulu17-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  java-common zulu17-ca-doc zulu17-ca-jdk zulu17-ca-jdk-headless zulu17-ca-jre
  zulu17-ca-jre-headless zulu17-doc zulu17-jdk-headless zulu17-jre
  zulu17-jre-headless
Suggested packages:
  default-jre
The following NEW packages will be installed:
  java-common zulu17-ca-doc zulu17-ca-jdk zulu17-ca-jdk-headless zulu17-ca-jre
  zulu17-ca-jre-headless zulu17-doc zulu17-jdk zulu17-jdk-headless zulu17-jre
  zulu17-jre-headless
0 upgraded, 11 newly installed, 0 to remove and 191 not upgraded.
Need to get 119 MB of archives.
After this operation, 282 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 java-common all 0.72build2 [6,782 B]
Get:2 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-ca-doc amd64 17.0.10-1 [143 kB]
Get:3 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-ca-jre-headless amd64 17.0.10-1 [40.0 MB]
Get:4 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-ca-jre amd64 17.0.10-1 [318 kB]
Get:5 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-ca-jdk-headless amd64 17.0.10-1 [78.2 MB]
Get:6 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-ca-jdk amd64 17.0.10-1 [11.4 kB]
Get:7 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-doc amd64 17.0.10-1 [2,930 B]
Get:8 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-jre-headless amd64 17.0.10-1 [2,950 B]
Get:9 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-jre amd64 17.0.10-1 [2,944 B]
Get:10 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-jdk-headless amd64 17.0.10-1 [2,960 B]
Get:11 https://repos.azul.com/zulu/deb stable/main amd64 zulu17-jdk amd64 17.0.10-1 [2,958 B]
Fetched 119 MB in 11s (10.7 MB/s)                                              
Selecting previously unselected package java-common.
(Reading database ... 200087 files and directories currently installed.)
Preparing to unpack .../00-java-common_0.72build2_all.deb ...
Unpacking java-common (0.72build2) ...
Selecting previously unselected package zulu17-ca-doc.
Preparing to unpack .../01-zulu17-ca-doc_17.0.10-1_amd64.deb ...
Unpacking zulu17-ca-doc (17.0.10-1) ...
Selecting previously unselected package zulu17-ca-jre-headless.
Preparing to unpack .../02-zulu17-ca-jre-headless_17.0.10-1_amd64.deb ...
Unpacking zulu17-ca-jre-headless (17.0.10-1) ...
Selecting previously unselected package zulu17-ca-jre.
Preparing to unpack .../03-zulu17-ca-jre_17.0.10-1_amd64.deb ...
Unpacking zulu17-ca-jre (17.0.10-1) ...
Selecting previously unselected package zulu17-ca-jdk-headless.
Preparing to unpack .../04-zulu17-ca-jdk-headless_17.0.10-1_amd64.deb ...
Unpacking zulu17-ca-jdk-headless (17.0.10-1) ...
Selecting previously unselected package zulu17-ca-jdk.
Preparing to unpack .../05-zulu17-ca-jdk_17.0.10-1_amd64.deb ...
Unpacking zulu17-ca-jdk (17.0.10-1) ...
Selecting previously unselected package zulu17-doc.
Preparing to unpack .../06-zulu17-doc_17.0.10-1_amd64.deb ...
Unpacking zulu17-doc (17.0.10-1) ...
Selecting previously unselected package zulu17-jre-headless.
Preparing to unpack .../07-zulu17-jre-headless_17.0.10-1_amd64.deb ...
Unpacking zulu17-jre-headless (17.0.10-1) ...
Selecting previously unselected package zulu17-jre.
Preparing to unpack .../08-zulu17-jre_17.0.10-1_amd64.deb ...
Unpacking zulu17-jre (17.0.10-1) ...
Selecting previously unselected package zulu17-jdk-headless.
Preparing to unpack .../09-zulu17-jdk-headless_17.0.10-1_amd64.deb ...
Unpacking zulu17-jdk-headless (17.0.10-1) ...
Selecting previously unselected package zulu17-jdk.
Preparing to unpack .../10-zulu17-jdk_17.0.10-1_amd64.deb ...
Unpacking zulu17-jdk (17.0.10-1) ...
Setting up java-common (0.72build2) ...
Setting up zulu17-ca-doc (17.0.10-1) ...
Setting up zulu17-ca-jre-headless (17.0.10-1) ...
update-alternatives: using /usr/lib/jvm/zulu17/bin/java to provide /usr/bin/java
 (java) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jfr to provide /usr/bin/jfr (
jfr) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/keytool to provide /usr/bin/k
eytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/rmiregistry to provide /usr/b
in/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jar to provide /usr/bin/jar (
jar) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jarsigner to provide /usr/bin
/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javac to provide /usr/bin/jav
ac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javadoc to provide /usr/bin/j
avadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javap to provide /usr/bin/jav
ap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jcmd to provide /usr/bin/jcmd
 (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdb to provide /usr/bin/jdb (
jdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeprscan to provide /usr/bin
/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeps to provide /usr/bin/jde
ps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jhsdb to provide /usr/bin/jhs
db (jhsdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jimage to provide /usr/bin/ji
mage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jinfo to provide /usr/bin/jin
fo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jlink to provide /usr/bin/jli
nk (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmap to provide /usr/bin/jmap
 (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmod to provide /usr/bin/jmod
 (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jpackage to provide /usr/bin/
jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jps to provide /usr/bin/jps (
jps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jrunscript to provide /usr/bi
n/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jshell to provide /usr/bin/js
hell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstack to provide /usr/bin/js
tack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstat to provide /usr/bin/jst
at (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstatd to provide /usr/bin/js
tatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/serialver to provide /usr/bin
/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jconsole to provide /usr/bin/
jconsole (jconsole) in auto mode
Setting up zulu17-ca-jdk-headless (17.0.10-1) ...
update-alternatives: using /usr/lib/jvm/zulu17/bin/java to provide /usr/bin/java
 (java) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jfr to provide /usr/bin/jfr (
jfr) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/keytool to provide /usr/bin/k
eytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/rmiregistry to provide /usr/b
in/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jar to provide /usr/bin/jar (
jar) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jarsigner to provide /usr/bin
/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javac to provide /usr/bin/jav
ac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javadoc to provide /usr/bin/j
avadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javap to provide /usr/bin/jav
ap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jcmd to provide /usr/bin/jcmd
 (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdb to provide /usr/bin/jdb (
jdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeprscan to provide /usr/bin
/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeps to provide /usr/bin/jde
ps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jhsdb to provide /usr/bin/jhs
db (jhsdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jimage to provide /usr/bin/ji
mage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jinfo to provide /usr/bin/jin
fo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jlink to provide /usr/bin/jli
nk (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmap to provide /usr/bin/jmap
 (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmod to provide /usr/bin/jmod
 (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jpackage to provide /usr/bin/
jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jps to provide /usr/bin/jps (
jps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jrunscript to provide /usr/bi
n/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jshell to provide /usr/bin/js
hell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstack to provide /usr/bin/js
tack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstat to provide /usr/bin/jst
at (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstatd to provide /usr/bin/js
tatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/serialver to provide /usr/bin
/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jconsole to provide /usr/bin/
jconsole (jconsole) in auto mode
Setting up zulu17-doc (17.0.10-1) ...
Setting up zulu17-ca-jre (17.0.10-1) ...
update-alternatives: using /usr/lib/jvm/zulu17/bin/java to provide /usr/bin/java
 (java) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jfr to provide /usr/bin/jfr (
jfr) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/keytool to provide /usr/bin/k
eytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/rmiregistry to provide /usr/b
in/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jar to provide /usr/bin/jar (
jar) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jarsigner to provide /usr/bin
/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javac to provide /usr/bin/jav
ac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javadoc to provide /usr/bin/j
avadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javap to provide /usr/bin/jav
ap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jcmd to provide /usr/bin/jcmd
 (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdb to provide /usr/bin/jdb (
jdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeprscan to provide /usr/bin
/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeps to provide /usr/bin/jde
ps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jhsdb to provide /usr/bin/jhs
db (jhsdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jimage to provide /usr/bin/ji
mage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jinfo to provide /usr/bin/jin
fo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jlink to provide /usr/bin/jli
nk (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmap to provide /usr/bin/jmap
 (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmod to provide /usr/bin/jmod
 (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jpackage to provide /usr/bin/
jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jps to provide /usr/bin/jps (
jps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jrunscript to provide /usr/bi
n/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jshell to provide /usr/bin/js
hell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstack to provide /usr/bin/js
tack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstat to provide /usr/bin/jst
at (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstatd to provide /usr/bin/js
tatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/serialver to provide /usr/bin
/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jconsole to provide /usr/bin/
jconsole (jconsole) in auto mode
Setting up zulu17-ca-jdk (17.0.10-1) ...
update-alternatives: using /usr/lib/jvm/zulu17/bin/java to provide /usr/bin/java
 (java) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jfr to provide /usr/bin/jfr (
jfr) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/keytool to provide /usr/bin/k
eytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/rmiregistry to provide /usr/b
in/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jar to provide /usr/bin/jar (
jar) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jarsigner to provide /usr/bin
/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javac to provide /usr/bin/jav
ac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javadoc to provide /usr/bin/j
avadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/javap to provide /usr/bin/jav
ap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jcmd to provide /usr/bin/jcmd
 (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdb to provide /usr/bin/jdb (
jdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeprscan to provide /usr/bin
/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jdeps to provide /usr/bin/jde
ps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jhsdb to provide /usr/bin/jhs
db (jhsdb) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jimage to provide /usr/bin/ji
mage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jinfo to provide /usr/bin/jin
fo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jlink to provide /usr/bin/jli
nk (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmap to provide /usr/bin/jmap
 (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jmod to provide /usr/bin/jmod
 (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jpackage to provide /usr/bin/
jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jps to provide /usr/bin/jps (
jps) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jrunscript to provide /usr/bi
n/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jshell to provide /usr/bin/js
hell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstack to provide /usr/bin/js
tack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstat to provide /usr/bin/jst
at (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jstatd to provide /usr/bin/js
tatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/serialver to provide /usr/bin
/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/zulu17/bin/jconsole to provide /usr/bin/
jconsole (jconsole) in auto mode
Setting up zulu17-jre-headless (17.0.10-1) ...
Setting up zulu17-jdk-headless (17.0.10-1) ...
Setting up zulu17-jre (17.0.10-1) ...
Setting up zulu17-jdk (17.0.10-1) ...
Processing triggers for man-db (2.10.2-1) ...
scott@scott-ThinkCentre-M910q:~$ java -version
openjdk version "17.0.10" 2024-01-16 LTS
OpenJDK Runtime Environment Zulu17.48+15-CA (build 17.0.10+7-LTS)
OpenJDK 64-Bit Server VM Zulu17.48+15-CA (build 17.0.10+7-LTS, mixed mode, sharing)
scott@scott-ThinkCentre-M910q:~$ sudo apt installzulu11-jdk
E: Invalid operation installzulu11-jdk
scott@scott-ThinkCentre-M910q:~$ ^C
scott@scott-ThinkCentre-M910q:~$ sudo apt install zulu11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  zulu11-ca-doc zulu11-ca-jdk zulu11-ca-jdk-headless zulu11-ca-jre zulu11-ca-jre-headless zulu11-doc
  zulu11-jdk-headless zulu11-jre zulu11-jre-headless
The following NEW packages will be installed:
  zulu11-ca-doc zulu11-ca-jdk zulu11-ca-jdk-headless zulu11-ca-jre zulu11-ca-jre-headless zulu11-doc zulu11-jdk
  zulu11-jdk-headless zulu11-jre zulu11-jre-headless
0 upgraded, 10 newly installed, 0 to remove and 191 not upgraded.
Need to get 115 MB of archives.
After this operation, 267 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-ca-doc amd64 11.0.22-1 [233 kB]
Get:2 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-ca-jre-headless amd64 11.0.22-1 [36.0 MB]
Get:3 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-ca-jre amd64 11.0.22-1 [326 kB]
Get:4 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-ca-jdk-headless amd64 11.0.22-1 [78.7 MB]
Get:5 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-ca-jdk amd64 11.0.22-1 [11.4 kB]                        
Get:6 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-doc amd64 11.0.22-1 [2,928 B]                           
Get:7 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-jre-headless amd64 11.0.22-1 [2,946 B]                  
Get:8 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-jre amd64 11.0.22-1 [2,944 B]                           
Get:9 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-jdk-headless amd64 11.0.22-1 [2,956 B]                  
Get:10 https://repos.azul.com/zulu/deb stable/main amd64 zulu11-jdk amd64 11.0.22-1 [2,954 B]                          
Fetched 115 MB in 13s (8,795 kB/s)                                                                                     
Selecting previously unselected package zulu11-ca-doc.
(Reading database ... 200676 files and directories currently installed.)
Preparing to unpack .../0-zulu11-ca-doc_11.0.22-1_amd64.deb ...
Unpacking zulu11-ca-doc (11.0.22-1) ...
Selecting previously unselected package zulu11-ca-jre-headless.
Preparing to unpack .../1-zulu11-ca-jre-headless_11.0.22-1_amd64.deb ...
Unpacking zulu11-ca-jre-headless (11.0.22-1) ...
Selecting previously unselected package zulu11-ca-jre.
Preparing to unpack .../2-zulu11-ca-jre_11.0.22-1_amd64.deb ...
Unpacking zulu11-ca-jre (11.0.22-1) ...
Selecting previously unselected package zulu11-ca-jdk-headless.
Preparing to unpack .../3-zulu11-ca-jdk-headless_11.0.22-1_amd64.deb ...
Unpacking zulu11-ca-jdk-headless (11.0.22-1) ...
Selecting previously unselected package zulu11-ca-jdk.
Preparing to unpack .../4-zulu11-ca-jdk_11.0.22-1_amd64.deb ...
Unpacking zulu11-ca-jdk (11.0.22-1) ...
Selecting previously unselected package zulu11-doc.
Preparing to unpack .../5-zulu11-doc_11.0.22-1_amd64.deb ...
Unpacking zulu11-doc (11.0.22-1) ...
Selecting previously unselected package zulu11-jre-headless.
Preparing to unpack .../6-zulu11-jre-headless_11.0.22-1_amd64.deb ...
Unpacking zulu11-jre-headless (11.0.22-1) ...
Selecting previously unselected package zulu11-jre.
Preparing to unpack .../7-zulu11-jre_11.0.22-1_amd64.deb ...
Unpacking zulu11-jre (11.0.22-1) ...
Selecting previously unselected package zulu11-jdk-headless.
Preparing to unpack .../8-zulu11-jdk-headless_11.0.22-1_amd64.deb ...
Unpacking zulu11-jdk-headless (11.0.22-1) ...
Selecting previously unselected package zulu11-jdk.
Preparing to unpack .../9-zulu11-jdk_11.0.22-1_amd64.deb ...
Unpacking zulu11-jdk (11.0.22-1) ...
Setting up zulu11-ca-jre-headless (11.0.22-1) ...
update-alternatives: using /usr/lib/jvm/zulu11/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
Setting up zulu11-ca-jre (11.0.22-1) ...
update-alternatives: using /usr/lib/jvm/zulu11/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
Setting up zulu11-jre-headless (11.0.22-1) ...
Setting up zulu11-ca-doc (11.0.22-1) ...
update-alternatives: using /usr/lib/jvm/zulu11/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
Setting up zulu11-doc (11.0.22-1) ...
Setting up zulu11-jre (11.0.22-1) ...
Setting up zulu11-ca-jdk-headless (11.0.22-1) ...
update-alternatives: using /usr/lib/jvm/zulu11/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
Setting up zulu11-ca-jdk (11.0.22-1) ...
update-alternatives: using /usr/lib/jvm/zulu11/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/zulu11/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
Setting up zulu11-jdk-headless (11.0.22-1) ...
Setting up zulu11-jdk (11.0.22-1) ...
scott@scott-ThinkCentre-M910q:~$ ^C
scott@scott-ThinkCentre-M910q:~$ ^C
scott@scott-ThinkCentre-M910q:~$



```

And here's my attempted uninstall: 
```
scott@scott-ThinkCentre-M910q:~$ java -version
openjdk version "17.0.10" 2024-01-16 LTS
OpenJDK Runtime Environment Zulu17.48+15-CA (build 17.0.10+7-LTS)
OpenJDK 64-Bit Server VM Zulu17.48+15-CA (build 17.0.10+7-LTS, mixed mode, sharing)
scott@scott-ThinkCentre-M910q:~$ sudo apt install gnupg ca-certificates curl

curl -s https://repos.azul.com/azul-repo.key | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg

echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" | sudo tee /etc/apt/sources.list.d/zulu.list
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ca-certificates is already the newest version (20230311ubuntu0.22.04.1).
curl is already the newest version (7.81.0-1ubuntu1.15).
gnupg is already the newest version (2.2.27-3ubuntu2.1).
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
File '/usr/share/keyrings/azul.gpg' exists. Overwrite? (y/N) N
Enter new filename: 
gpg: no valid OpenPGP data found.
gpg: dearmoring failed: File exists
deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main
scott@scott-ThinkCentre-M910q:~$ sudo apt remove <zulu17-jdk>
bash: syntax error near unexpected token `newline'
scott@scott-ThinkCentre-M910q:~$ sudo apt remove zulu17-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  zulu17-ca-doc zulu17-ca-jdk zulu17-ca-jdk-headless zulu17-doc
  zulu17-jdk-headless zulu17-jre zulu17-jre-headless
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  zulu17-jdk
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
After this operation, 25.6 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 202315 files and directories currently installed.)
Removing zulu17-jdk (17.0.10-1) ...
scott@scott-ThinkCentre-M910q:~$ java-version
java-version: command not found
scott@scott-ThinkCentre-M910q:~$ java -version
openjdk version "17.0.10" 2024-01-16 LTS
OpenJDK Runtime Environment Zulu17.48+15-CA (build 17.0.10+7-LTS)
OpenJDK 64-Bit Server VM Zulu17.48+15-CA (build 17.0.10+7-LTS, mixed mode, sharing)
scott@scott-ThinkCentre-M910q:~$ sudo apt install zulu11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
zulu11-jdk is already the newest version (11.0.22-1).
The following packages were automatically installed and are no longer required:
  zulu17-ca-doc zulu17-ca-jdk zulu17-ca-jdk-headless zulu17-doc
  zulu17-jdk-headless zulu17-jre zulu17-jre-headless
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
scott@scott-ThinkCentre-M910q:~$ java-version
java-version: command not found
scott@scott-ThinkCentre-M910q:~$ java -version
openjdk version "17.0.10" 2024-01-16 LTS
OpenJDK Runtime Environment Zulu17.48+15-CA (build 17.0.10+7-LTS)
OpenJDK 64-Bit Server VM Zulu17.48+15-CA (build 17.0.10+7-LTS, mixed mode, sharing)
scott@scott-ThinkCentre-M910q:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04


```

Any and all help appreciated!  
Best,
Scott

---

### Post by sks24 on 2024-03-04
It looks like I've got it. > scott@scott-ThinkCentre-M910q:~$ sudo update-alternatives --config java
[sudo] password for scott: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                 Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/zulu17/bin/java          2174801   auto mode
* 1            /usr/lib/jvm/zulu-11-amd64/bin/java   2117000   manual mode
  2            /usr/lib/jvm/zulu11/bin/java          2117001   manual mode
  3            /usr/lib/jvm/zulu17/bin/java          2174801   manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
scott@scott-ThinkCentre-M910q:~$ java -version
openjdk version "11.0.22" 2024-01-16 LTS
OpenJDK Runtime Environment Zulu11.70+15-CA (build 11.0.22+7-LTS)
OpenJDK 64-Bit Server VM Zulu11.70+15-CA (build 11.0.22+7-LTS, mixed mode)
scott@scott-ThinkCentre-M910q:~$ ^C


---

