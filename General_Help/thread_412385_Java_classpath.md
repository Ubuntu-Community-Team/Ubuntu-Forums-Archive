---
title: "Java classpath"
date: 2007-04-18
forum: General Help
---

### Post by gregsheu on 2007-04-18
I don't understand why the PATH and CLASSPATH environment variables are so hard to set in Ubuntu. I've tried in /home/me/.bashrc, /etc/environment and /etc/profile, none of them works.
I need to run Java with Oracle and this is how I set my PATH and CLASSPATH

JAVA_HOME="/usr/local/jdk1.6.0_01"
export JAVA_HOME
PATH="/usr/local/jdk1.6.0_01/bin"
export PATH
CLASSPATH="/usr/local/jdk1.6.0_01/lib/tools.jar:/usr/local/jdk1.6.0_01/jre/lib/ext/ojdbc14.jar"
export CLASSPATH

When I javac MyJava.java 
it shows this error 
error: error reading /usr/local/jdk1.6.0_01/jre/lib/ext/ojdbc14.jar; error in opening zip file

I don't understand what I am setting wrong. I have another Fedora and SuSE box, and they all work fine when I set those environment variables in /etc/profile, but it just doesn't work in Ubuntu. The reason why I use Ubuntu is because it has very good support and easy to install beryl for my graphic cards, but if this path can't work out, I guess I need to go back to Fedora again.  I have searched all around in this forum and google around, but I can't fins the solution. Hope you expert can help me out.  Thank you in advance!

---

### Post by amohanty on 2007-04-18
First off jars are simply compressed files. They just have a bunch of stuff in them. Its possible that that specific jar may be corrupted. Unlikely but possible. So to test that see if uncompressing it works.

Open a terminsal.

mkdir tmp
cd tmp
jar -xf /usr/local/jdk1.6.0_01/jre/lib/ext/ojdbc14.jar

This should uncompress it in tmp. If it can't you have a problem. Try reinstalling jdk6. 

Also I believe the default sun0jdk install on ubuntu via synaptic installs it in /usr/lib/jvm which is a link. How come yours is in /usr/local? Did you manually install it?

If so I would suggest using the sun-jdk in the universe repos.

HTH
AM

---

### Post by gregsheu on 2007-04-18
Thanks for the reply. Yes, I download it from Sun and manually intall it. /usr/local is the dir that I usually put the applications I manually install, such as mysql, tomcat, eclipse and others. I do this all the time in Fedora, but it doesn't create any issue in Fedora. Well, I don't like to compare Ubuntu with other distro, maybe this is the way that Ubuntu wants to make it more secure. The way that you describe makes my java program throws the sql exception not found, which means it can't find the Oracle jdbc classpath. Thanks!

---

### Post by amohanty on 2007-04-18
Heres and easy script for you to setup all jars in the classpath:

```

#! /bin/bash

export JAVA_HOME='/usr/lib/jvm/java-1.5.0-sun'

set_cp() {
  local jvm_jars=$(find $JAVA_HOME/ -iname "*.jar" -printf '%p:')
  local shr_jars=$(echo /usr/share/java/*.jar | sed 's/ /:/g')':'
  local loc_jars=$(echo /usr/local/share/java/*.jar | sed 's/ /:/g')':'
  export CLASSPATH=$(echo .:$jvm_jars$shr_jars$loc_jars)
}

ecp() {
  echo $CLASSPATH | sed 's/:/\n/g'
}

# set class path by default
set_cp


```

put it in a bash script. replace java_home with yours and put all third party jars you download in /usr/local/share/...

running ecp at the prompt will show you all the jars on your path.

HTH
AM

---

### Post by gregsheu on 2007-04-23
I guess I found the solution on debian.org since ubuntu is debian based.
check this. Now I can manually set my own JAVA_HOME, PATH and CLASSPATH. It works for me now. I will migrate to Ubuntu 7.04 for all my Linux.

[http://www.debian.org/doc/manuals/debian-java-faq/ch11.html](http://www.debian.org/doc/manuals/debian-java-faq/ch11.html) 

11.1.2 Making Java 2 work in Debian

If you wish to use Sun's or Blackdown's jdk 1.2 or later in Debian download the packages provided by Blackdown (they are available in aptable directories) from the different mirrors available in [http://www.blackdown.org/java-linux/mirrors.html](http://www.blackdown.org/java-linux/mirrors.html) (check the debian subdir). Currently there are i386 packages for the Java2 SDK and RE, JAI, Java3D and JMF. This is the recommended mechanism for more information read How can I get Debian packages from Blackdown?, Section 11.1.

Or you can download the archives yourself (that is, the tar.gz, no the .deb package) and use the following mechanism:

    * Make a directory under /usr/local (for example /usr/local/sun).

    * Download the archine into this directory, then unpack it. A directory jdk1.X [4] will be created.

    * Adjust the alternatives to work correctly:

              update-alternatives --install /usr/bin/javac javac /usr/local/sun/jdk1.X/bin/javac 120
              update-alternatives --install /usr/bin/java Java /usr/local/sun/jdk1.X/bin/java 120

    * Check your alternatives with "type"

              type javac
              type java

You should have now a fully working jdk 1.X environment, virtual machine and compiler included.

You might need to change your /etc/profile adding the proper definitions of some environment variables (CLASSPATH, JAVA_COMPILER and JAVA_HOME) so that Java programs can find the kit you just have installed. The following example show which settings you could add if you had installed Sun's 1.2.2 jdk:

     # JDK 1.2.2 (.tar)
     export CLASSPATH=.:/usr/local/sun/jdk1.2.2/lib:/usr/local/sun/jdk1.2.2/jre/lib
     export JAVA_COMPILER=javacomp
     export JAVA_HOME=/usr/local/sun/jdk1.2.2
     export PATH=$PATH:/usr/local/sun/jdk1.2.2/bin

Note: As Juergen Kreileder correctly pointed me out The preferred name for versions >= 1.2 is Java 2 SE (Standard Edition). The jdk1.3 now is called "Java2 SDK v1.3" or "J2SDK 1.3". The jre1.3 now is called "Java2 RE v1.3" or "J2RE 1.3".

---

