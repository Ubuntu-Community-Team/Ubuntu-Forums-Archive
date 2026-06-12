---
title: "Installing java.."
date: 2004-11-04
forum: General Help
---

### Post by Verlager on 2004-11-04
There is a quick how-to regarding installing java for Firefox. It has small errors, however:> 
[COLOR=DarkGreen]sudo chmod a+x j2re-1_4_2_05-linux-i586.bin 
./j2re-1_4_2_05-linux-i586.bin[/COLOR]
[COLOR=DarkRed]sudo mv j2re-1_4_2_05 /usr/local/[/COLOR]

[COLOR=Navy]Verlager note: (whoops! the dir name is actually _ j2re1.4.2_05_ so the command should be: sudo mv j2re1.4.2_05 /usr/local/  [/COLOR]

cd /home/username/.mozilla/plugins
ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.soWell, whatever. Just a simple oversight. But now, I have a program that needs java. So I edited /etc/profile to include this:
PATH="/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/lib/j2re1.4.2_05/bin"

But! When I reboot and type:** $PATH** I get: verlager@ubuntu:~ $ $PATH
**bash: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games: No such file or directory**
verlager@ubuntu:~ $

Where the heck is this path coming from? I need to edit it to correct it and append the path somehow in my /home/verlager dir. Any ideas? Maybe  I should be appending the general path with my user path :/usr/lib/j2re1.4.2_05/bin part of the path to the general path, as in: $PATH=$PATH+":/usr/lib/j2re1.4.2_05/bin", or something like that

---

### Post by triad169 on 2004-11-04
This works for me.

sudo ln -sf /usr/local/j2re-1_4_2_05/bin/java /usr/bin/java

sudo ln -sf /usr/local/j2re-1_4_2_05/bin/java_vm /usr/bin/java_vm

creates symbolic links to your java executables into the sytem executable path.

Triad

---

### Post by ubuntu-geek on 2004-11-04
That how is only for getting java to work in firefox not systemwide. If you wish to have java installed system wide check out the java howto on the wiki..
 
 [http://www.ubuntulinux.org/wiki/Java]("http://www.ubuntulinux.org/wiki/Java")
 
 EDIT: Or do what triad169 said :)

---

### Post by Verlager on 2004-11-04
[QUOTE=triad169]This works for me.

sudo ln -sf /usr/local/j2re-1_4_2_05/bin/java /usr/bin/java

sudo ln -sf /usr/local/j2re-1_4_2_05/bin/java_vm /usr/bin/java_vm

creates symbolic links to your java executables into the sytem executable path.

Triad[/QUOTE]
 Oh, my God! It worked! Thank you so much, Triad!

---

### Post by Verlager on 2004-11-05
Installing java: download the [main file from Sun](http://java.sun.com/webapps/download/AutoDL?BundleId=97): and save it to your home directory, then: 
[COLOR=DarkGreen]
[B]sudo chmod a+x j2re-1_4_2_05-linux-i586.bin
./j2re-1_4_2_05-linux-i586.bin
sudo mv j2re1.4.2_05 /usr/local/ 
sudo ln -sf /usr/local/j2re1.4.2_05/bin/java /usr/bin/java
sudo ln -sf /usr/local/j2re1.4.2_05/bin/java_vm /usr/bin/java_vm
java -version[/B][/COLOR]

Note: this will not allow Firefox browser to run java. Your comments and suggestions are most welcome. Thanks to ubuntu-geek and Triad for this info.

---

### Post by jwenting on 2004-11-05
The installation instructions on [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) (yes, download the latest, 1.4.2 was replaced about a month ago) tell you how to achieve browser plugin mode as well.

Download: [http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jdk-1.5.0-oth-JPR&SiteId=JSC&TransactionId=noreg](http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jdk-1.5.0-oth-JPR&SiteId=JSC&TransactionId=noreg)

Installation manual: [http://java.sun.com/j2se/1.5.0/install.html](http://java.sun.com/j2se/1.5.0/install.html)
instructions for Mozilla (I guess those work more or less for FireFox as well as it's Mozilla derived): [http://java.sun.com/j2se/1.5.0/manual_install_linux.html](http://java.sun.com/j2se/1.5.0/manual_install_linux.html) 

Note this installs the compiler as well. Java is a great language, good chance to meet it if you haven't before :)

For just the runtime, the following URLs apply:
[http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0-oth-JPR&SiteId=JSC&TransactionId=noreg](http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0-oth-JPR&SiteId=JSC&TransactionId=noreg)
[http://java.sun.com/j2se/1.5.0/jre/install-linux.html](http://java.sun.com/j2se/1.5.0/jre/install-linux.html)

---

### Post by Verlager on 2004-11-05
[COLOR=DarkGreen][B]chmod +x jre-1_5_0-linux-i586.bin
./jre-1_5_0-linux-i586.bin
sudo mv jre1.5.0/ /usr/local
sudo rm /usr/bin/java
sudo rm /usr/bin/java_vm
sudo ln -sf /usr/local/jre1.5.0/bin/java_vm /usr/bin/java_vm
sudo ln -sf /usr/local/jre1.5.0/bin/java /usr/bin/java
java -version[/B][/COLOR]

java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0-b64)
Java HotSpot(TM) Client VM (build 1.5.0-b64, mixed mode, sharing)
user@ubuntu:~ $

---

### Post by jwenting on 2004-11-05
Did pretty much that except install it in /opt/jdk1.5.0 with a symlink to /opt/java (just my preference) and the bin for the JDK was already executable.

Don't forget to add 
[COLOR=DarkGreen][B]JAVA_HOME=/opt/java # or whatever you made the symlink to
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
[/B][/COLOR]
to ~.bashrc (or the equivalent file in /etc for all users) to make the shell see it globally

---

### Post by diebels on 2004-11-05
What about

Download java from 
[sun java 1.5](http://java.sun.com/j2se/1.5.0/download.jsp) 

Install needed packages:
# sudo apt-get install java-package sun-j2sdk1.5debian galternatives

Download 1.5 patch to java-package from: [serios.net](http://serios.net/files/patch-java-package_0.14.tar.gz)

Apply it: 
# tar zxvf patch-java-package_0.14.tar.gz
# cd patch-java-package
# sudo ./patch-java-package.sh

Make .deb java package and install it:
# fakeroot make-jpkg jre-1_5_0-linux-i586.bin
# dpkg -i sun-j2re1.5_1.5.0_i386.deb

Run galternatives to set browser plugin and stuff:
# gksudo galternatives

---

