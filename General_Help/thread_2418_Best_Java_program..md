---
title: "Best Java program."
date: 2004-10-28
forum: General Help
---

### Post by akamjballar on 2004-10-28
Hello, I have been using ubuntu for about 2 months now. I haven't found any program that i can code in java with. I am looking for something that I can find via get-apt. Any java development program would be good.

Thank you.

---

### Post by JProgrammer on 2004-10-28
[QUOTE=akamjballar]Hello, I have been using ubuntu for about 2 months now. I haven't found any program that i can code in java with. I am looking for something that I can find via get-apt. Any java development program would be good.

Thank you.[/QUOTE]
 Well then you need the best IDE around [eclipse](www.eclipse.org) this project is going great guns and once you code with it you wont know what you ever did without it. Please note if you need Java 5 (1.5) support you will need a pre-release of 3.1 no the 3.0 release.

---

### Post by akamjballar on 2004-10-28
I don't really need 1.5 support. How can I install ecplise. I am not very good with Linux, I just started out 2 months ago. I just know how to do basic things, is there a way I can get it via apt-get.

---

### Post by shufla on 2004-10-28
Hello,

[QUOTE=akamjballar]I don't really need 1.5 support. How can I install ecplise. I am not very good with Linux, I just started out 2 months ago. I just know how to do 
basic things, is there a way I can get it via apt-get.[/QUOTE]

Go thru install documentation of eclipse. There is chapter assigned to linux-based installs.

Best regards,
Lukasz Nowak

---

### Post by akamjballar on 2004-10-28
Thank you, I will look into that. Is there anything I can use in the quick time. I just need something really fast that I can install via apt-get. Since, it would take me time to read the documentation.

---

### Post by shufla on 2004-10-28
Hello,

[QUOTE=akamjballar]Thank you, I will look into that. Is there anything I can use in the quick time. I just need something really fast that I can install via apt-get. Since, it would take me time to read the documentation.[/QUOTE]

Shame on me :> For your own responsibility you may add `multiverse' repository to apt. It's easy. As root (sudoing) edit /etc/apt/sources.list then copy 2 lines with universe, and substitute in second pair word universe to multiverse. Then run synaptic, ignore error, Update/Rehresh repository and search for eclipse.

I haven't tried it, but it should work.

Best regards,
Lukasz Nowak

---

### Post by JProgrammer on 2004-10-28
[QUOTE=akamjballar]Thank you, I will look into that. Is there anything I can use in the quick time. I just need something really fast that I can install via apt-get. Since, it would take me time to read the documentation.[/QUOTE]
 Quick and dirty then you can always use vim or even gedit both have java syntax highlighting and with your Sun sdk and a CLI you can code to your hearts content

---

### Post by elwis on 2004-10-28
[QUOTE=JProgrammer]Quick and dirty then you can always use vim or even gedit both have java syntax highlighting and with your Sun sdk and a CLI you can code to your hearts content[/QUOTE]
 Exactly, gvim or emacs is good enough for sure, that's what i use. 
Another alternative would be jedit which has a lot of available plug-ins.

I can definietly recommend Eclipse though. It eats a lot of resoursec, but it's great. And, if your going GUI, take a look at the visual Eclipse Editor, where you can create your SWT and Swing forms in a matter of seconds ;)
[http://eclipse.org/vep/](http://eclipse.org/vep/)

---

### Post by akamjballar on 2004-10-28
Please teach me how to install it. I have no idea on how to install it. :)

---

### Post by elwis on 2004-10-29
[QUOTE=akamjballar]Please teach me how to install it. I have no idea on how to install it. :)[/QUOTE]
 Install what? Eclipse? Or gvim?

You don't install eclipse, you unzip it where you want it, jump into "eclipse" folder and execute ./eclipse :)
(download from here, get the newest available)
[http://eclipse.org/downloads/index.php](http://eclipse.org/downloads/index.php)

gvim, you install through apt-get :)

---

### Post by shufla on 2004-10-29
Hi,

[QUOTE=elwis]
...
gvim, you install through apt-get :)[/QUOTE]

eclipse also...from multiverse

Best regards,
Lukasz Nowak

---

### Post by elwis on 2004-10-29
[QUOTE=shufla]Hi,



eclipse also...from multiverse

Best regards,
Lukasz Nowak[/QUOTE]
 But last time I checked, that was an old version. 3.0.1 is the stable, if you want to run Jdk.1.5 you need 3.1M2 build.

---

### Post by Johan on 2004-10-29
[QUOTE=shufla]Hello,

Shame on me :> For your own responsibility you may add `multiverse' repository to apt. It's easy. As root (sudoing) edit /etc/apt/sources.list then copy 2 lines with universe, and substitute in second pair word universe to multiverse. Then run synaptic, ignore error, Update/Rehresh repository and search for eclipse.

I haven't tried it, but it should work.

Best regards,
Lukasz Nowak[/QUOTE]

I have added both universe and multiverse repositories to /etc/apt/sources.list but eclipse doesn't seem to exist in there either. Shouldn't it be there, since it's in debian unstable?

---

### Post by elwis on 2004-10-29
[QUOTE=Johan]I have added both universe and multiverse repositories to /etc/apt/sources.list but eclipse doesn't seem to exist in there either. Shouldn't it be there, since it's in debian unstable?[/QUOTE]
 did you do an apt-get update?

elwis@ubuntu:~ $ apt-cache search eclipse
eclipse-javac - Eclipse Java compiler and ant plug-in
eclipse-jdt - Java Development Tools plug-ins for Eclipse
eclipse-nls-sdk - localized message catalog for eclipse
eclipse-pde - Plug-in Development Environment to develop Eclipse plug-ins
eclipse-platform - Eclipse platform without plug-ins to develop any language
eclipse-sdk - Extensible Tool Platform and Java IDE
eclipse-source - Eclipse source code plug-ins
eclipse-webdav-ftp - Eclipse FTP and WebDAV Support
libeclipse-jni - Platform dependend files for eclipse-platform
libswt2.1-gtk2-java - Fast and rich GUI toolkit for Java, gtk2 version
libswt2.1-motif-java - Fast and rich GUI toolkit for Java, motif version
libswt-pocketpc3-java - Standard Widget Toolkit for PocketPC JAR library
libswt-pocketpc3-jni - Standard Widget Toolkit for PocketPC JNI library

---

### Post by Johan on 2004-10-30
I've recently started to use Ubuntu instead of debian so I might be doing something wrong. Below is my sources.list and a search...

root@Lillan:/home/johan # cat /etc/apt/sources.list | grep deb
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb [http://people.ubuntu.com/~daniels/](http://people.ubuntu.com/~daniels/) x40/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb [http://people.ubuntu.com/~jdub/warty/](http://people.ubuntu.com/~jdub/warty/) ./

root@Lillan:/home/johan # apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) x40/ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) x40/ Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Reading Package Lists... Done

root@Lillan:/home/johan # apt-cache search eclipse
eclipse-nls-sdk - localized message catalog for eclipse
libswt-pocketpc3-java - Standard Widget Toolkit for PocketPC JAR library
libswt-pocketpc3-jni - Standard Widget Toolkit for PocketPC JNI library

root@Lillan:/home/johan #

---

