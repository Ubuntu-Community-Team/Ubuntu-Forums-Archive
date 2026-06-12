---
title: "JAVA issues with apache's coccon"
date: 2005-03-22
forum: General Help
---

### Post by nmalnati on 2005-03-22
Hi all-

Thanks for any help in advance.  

I can't get Apache's Cocoon to work with my java.  Apparently JAVA_HOME isn't properly setup.  I eventually want to modify my /etc/bash.bashrc file, but first, I want to know what settings I really need to put in for everything to work.  

Since java can't be packaged initally, I install Sun's Java 1.4.2.  (1.5 doesn't want to build cocoon).  I get the error that my Java environment hasn't yet been setup after typing ./cocoon servlet.

I have cocoon working in Mac OSX with a bashrc file. Because ubuntu's file structure  is different, things don't work...
-----------------------------------------------
CONSOLE OUTPUT
-----------------------------------------------

root@altius:/home/nmalnati # cd /usr/share/cocoon-2.1.6/
root@altius:/usr/share/cocoon-2.1.6 # ./cocoon.sh servlet
You must set JAVA_HOME to point at your Java Development Kit installation
root@altius:/usr/share/cocoon-2.1.6 # java -version
java version "1.4.2_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_06-b03)
Java HotSpot(TM) Client VM (build 1.4.2_06-b03, mixed mode)
root@altius:/usr/share/cocoon-2.1.6 # whereis java
java: /usr/bin/java /usr/share/java /usr/share/man/man1/java.1.gz
root@altius:/usr/share/cocoon-2.1.6 # ls -l /usr/bin/java
lrwxrwxrwx    1 root     root           22 2005-03-21 22:22
/usr/bin/java -> /etc/alternatives/java

root@altius:/usr/share/cocoon-2.1.6 # cd /etc/alternatives/

lrwxrwxrwx    1 root     root           30 2005-03-21 22:22 java ->
/usr/lib/j2sdk1.4-sun/bin/java

root@altius:/etc/alternatives # echo $JAVA_HOME

root@altius:/home/nmalnati # JAVA_HOME=/usr/lib/j2sdk1.4-sun/bin/java
root@altius:/home/nmalnati # echo $JAVA_HOME
/usr/lib/j2sdk1.4-sun/bin/java
root@altius:/etc/alternatives # echo $PATH
/sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin
root@altius:/home/nmalnati # PATH=$JAVA_HOME/bin
root@altius:/home/nmalnati # echo $PATH
/usr/lib/j2sdk1.4-sun/bin/java/bin

root@altius:/etc/alternatives # cd /usr/share/cocoon-2.1.6/
root@altius:/usr/share/cocoon-2.1.6 # ./cocoon.sh servlet
You must set JAVA_HOME to point at your Java Development Kit installation
root@altius:/usr/share/cocoon-2.1.6 #
---------------------------------------------------

I am to assume the following is correct:
$JAVA_HOME=/usr/lib/j2sdk1.4-sun/bin/java
$PATH=/usr/lib/j2sdk1.4-sun/bin/java/bin

This is Cocoon's official set of instructions: [http://cocoon.apache.org/2.1/installing/index.html#Set+JAVA_HOME+environment+variable](http://cocoon.apache.org/2.1/installing/index.html#Set+JAVA_HOME+environment+variable)

Again, any help would be appreciated!

-=Nick

---

### Post by nmalnati on 2005-03-22
OK, this is actually a quick and dirty fix, but it works. Also there is now no need to edit my bashrc.  I hope this helps for anyone trying to setup cocoon and having issues. 

I went into 'cocoon.sh' and added the following line:

JAVA_HOME=/usr/lib/j2sdk1.4-sun

That's it...

---

