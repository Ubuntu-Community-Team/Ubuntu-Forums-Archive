---
title: "Mplayer"
date: 2005-10-26
forum: General Help
---

### Post by 3dmaker on 2005-10-26
I have just moved from Fedora Core 4 to Ubuntu to try something new. First of all FC4 had this nice thing called yum. I insatlled yum extender wich allowed me to see the things that I have installed, and what other packages i dont. I dont see anything at all like this under Ubuntu. How am I supposed to install things? Second... Can i insatll Mplayer? I need to listen to my music... But i cant because apt-get install mplayer does not work. This is pretty frustrating...
Edit: I have found the install/remove GUI application

---

### Post by Qrk on 2005-10-26
Ubuntu uses apt, which has frontend synaptic. You can get it via
System-> Administration-> Synapic Package Manager 

Another good way to add applications is through the tool at the bottom of the applications menu.

You can install mplayer after adding the extra repositories. That is documented in the starter guide, inside the help. (look on the bottom of the first help page)

---

### Post by Iandefor on 2005-10-26
Ubuntu has a similar package called [Synaptic]("https://wiki.ubuntu.com/SynapticHowto"). Try [enabling extra repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") and try apt-get again. Or, you can open up synaptic and find it there.

---

### Post by gillion on 2005-10-26
[QUOTE=3dmaker]I have just moved from Fedora Core 4 to Ubuntu to try something new. First of all FC4 had this nice thing called yum. I insatlled yum extender wich allowed me to see the things that I have installed, and what other packages i dont. I dont see anything at all like this under Ubuntu. How am I supposed to install things? Second... Can i insatll Mplayer? I need to listen to my music... But i cant because apt-get install mplayer does not work. This is pretty frustrating...
Edit: I have found the install/remove GUI application[/QUOTE]

Please read the installation guid that is on your install CD.

It will explain how you can extend your software list by adding more software repositories (locations) to the apt system.

You have 3 main methods to install applications on ubuntu.

**apt**

and

**synaptic**

and

**add/remove softare**

The last 2 are inthe menus of your GUI

secondly ... in order to extend please turn on the repository links in the menu item listed under synaptic

ALL OF THIS is clearly explained in the starter guide.

---

### Post by 3dmaker on 2005-10-26
Thanks you everyone for being nice and not flaming me. I have setup the repositorys in the Synaptic manager, but I still do not see Mplayer anywhere. I ran a search and it only finds mga-vid-source. What should I do?

---

### Post by Xisiqomelir on 2005-10-26
[QUOTE=3dmaker]Thanks you everyone for being nice and not flaming me. I have setup the repositorys in the Synaptic manager, but I still do not see Mplayer anywhere. I ran a search and it only finds mga-vid-source. What should I do?[/QUOTE]

Follow the linked guides again, check your setup, then search again.

or:

1) Edit the apt sources list by hand

2) Compile from source ([Linkity](http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre7try2.tar.bz2))

---

### Post by 3dmaker on 2005-10-26
[QUOTE=Xisiqomelir]Follow the linked guides again, check your setup, then search again.

or:

1) Edit the apt sources list by hand

2) Compile from source ([Linkity](http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre7try2.tar.bz2))[/QUOTE]

I would compile from source, but Ubuntu doesnt have a "make" command. Or a C++ compiler...

---

### Post by Moriak on 2005-10-26
They are not installed by default. I guess they are not because most of Ubuntu users don't need to manually compile applications. Thanks to apt / synaptic. 

Use **Synaptic or Add Applications** to install **make** and **gcc**. (You should re-read gillion's post)

Applications -> Add Programs -> File -> Advanced

Click Search to find "make", and "gcc" packages.

Mark them both for installation. (right click)

Click Apply.

Synaptic will install everything for you.

You should now be able to ./configure, make, make install.

Jonathan

---

### Post by jerrybme on 2005-10-26
"apt-get install build-essential " will install all the general packages needed to compile, headers, make, gcc & others.

---

