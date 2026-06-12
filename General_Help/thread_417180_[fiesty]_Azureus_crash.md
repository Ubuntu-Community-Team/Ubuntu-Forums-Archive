---
title: "[fiesty] Azureus crash"
date: 2007-04-21
forum: General Help
---

### Post by drolyk on 2007-04-21
Hi All!

I`ve got azureus and sun-java5 installed on fiesty. When I`m trying to launch azureus it gives me segfaults everytime.

$ azureus 
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0374172, pid=8863, tid=3084502720
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid8863.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


I really disappointed with this behavior. What I need to do to launch azureus successfully ?

Thanks

---

### Post by josephus on 2007-04-21
where did you get azureus from?  the copy from the repo for some reason is very prone to crashes.  get it directly from:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

---

### Post by Red Knuckles on 2007-04-21
You can change which java you use. Run:

sudo update-alternatives --config java 

and in my case I have:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
 

and choose option 3 instead of 1 and Azureus stays open. OR if you DO want to use latest version of Sun-Java you could run:

sudo aptitude purge azureus

Then Download Azureus  tar ball at Azureus website:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

I downloaded to /home/me and then ran:

@localhost:~$sudo mv Azureus_2.5.0.4_linux.tar.bz2 /usr/bin
@localhost:~$cd /usr/bin
@localhost:/usr/bin$sudo tar -xjvf Azureus_2.5.0.4_linux.tar.bz2
@localhost:/usr/bin$sudo rm *.bz2

Then in K-Menu Editor [or whatever in Gnome] change whatever the old commcand for the Azureus entry to '/usr/bin/azureus/azureus'. You will now have to run updates from within Azureus as root, ie. 'sudo /usr/bin/azureus/azureus'.  And now your Azureus will stay open and use latest version of Sun-Java!
:guitar: 
:lolflag:

---

### Post by Gray Fox on 2007-04-27
> **Red Knuckles said:**
> You can change which java you use. Run:

sudo update-alternatives --config java 

and in my case I have:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
 

and choose option 3 instead of 1 and Azureus stays open. OR if you DO want to use latest version of Sun-Java you could run:

sudo aptitude purge azureus

Then Download Azureus  tar ball at Azureus website:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

I downloaded to /home/me and then ran:

@localhost:~$sudo mv Azureus_2.5.0.4_linux.tar.bz2 /usr/bin
@localhost:~$cd /usr/bin
@localhost:/usr/bin$sudo tar -xjvf Azureus_2.5.0.4_linux.tar.bz2
@localhost:/usr/bin$sudo rm *.bz2

Then in K-Menu Editor [or whatever in Gnome] change whatever the old commcand for the Azureus entry to '/usr/bin/azureus/azureus'. You will now have to run updates from within Azureus as root, ie. 'sudo /usr/bin/azureus/azureus'.  And now your Azureus will stay open and use latest version of Sun-Java!
:guitar: 
:lolflag:

Thanks!!  :D 

I switched from Sun Java to ... whatever else it was that I had on my install and now Azureus isn't crashing.  ...For now!

---

### Post by lawahdy on 2007-05-03
> **Red Knuckles said:**
> You can change which java you use. Run:

sudo update-alternatives --config java 

and in my case I have:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
 

and choose option 3 instead of 1 and Azureus stays open. OR if you DO want to use latest version of Sun-Java you could run:

sudo aptitude purge azureus

Then Download Azureus  tar ball at Azureus website:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

I downloaded to /home/me and then ran:

@localhost:~$sudo mv Azureus_2.5.0.4_linux.tar.bz2 /usr/bin
@localhost:~$cd /usr/bin
@localhost:/usr/bin$sudo tar -xjvf Azureus_2.5.0.4_linux.tar.bz2
@localhost:/usr/bin$sudo rm *.bz2

Then in K-Menu Editor [or whatever in Gnome] change whatever the old commcand for the Azureus entry to '/usr/bin/azureus/azureus'. You will now have to run updates from within Azureus as root, ie. 'sudo /usr/bin/azureus/azureus'.  And now your Azureus will stay open and use latest version of Sun-Java!
:guitar: 
:lolflag:

just wanna thank you .. this helped me a lot..

cheers

---

### Post by Red Knuckles on 2007-05-04
> **lawahdy said:**
> just wanna thank you .. this helped me a lot..

cheers

Glad to help a fellow Ubuntu user. I've received lots of help from others.:popcorn:

---

### Post by Montsegur87 on 2007-05-17
Im having the same problem. The reason I havent done this yet is that I dont know if I will keep al the configuration after the "reinstall" (Im afraid to lose a 90% downloaded torrent)

---

### Post by TheDudeAbides on 2007-10-14
will the reinstall destroy all current download progress?

---

### Post by retrow on 2007-10-22
> sudo update-alternatives --config java

This option worked for me! I had to go for something named cacao package which provided files for Java.

> will the reinstall destroy all current download progress?
In my case the downloads resumed right from the point where Azureus had earlier crashed. So no. It doesn't destroy the files that were/are in under progress.

---

### Post by OpticalIllusion on 2007-10-22
Azureus was crashing on me as well and after some searching I found that downloading a new jar file from here:
[http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download](http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download)

And repacing the existing /usr/share/java/Azureus2.jar with the new one you downloaded (and renaming it to Azureus2.jar of course) fixed my problem.

---

### Post by taavi on 2007-10-24
I get the same crash in Gutsy ... Is there way solve this within Ubuntu, not dowloading original Azureus from SF.

EDIT: sudo apt-get install cacao && sudo update-alternatives --config java  may do the trick. But for me it's horribly slow, so I'm open to better suggestions how to get it working with Sun Java.

---

