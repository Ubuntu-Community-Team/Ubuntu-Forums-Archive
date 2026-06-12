---
title: "I can not install java 7 on ubuntu 19.10 , help"
date: 2020-02-12
forum: General Help
---

### Post by anje2 on 2020-02-12
hi guys I need help , to play bluray disc movie I will need to have something like ( power DVD ) which it dosnt work on Ubuntu, so I decided to use alternative software such as ( vlc player ) and to play bluray it need to install ( java ) , is there any way to install java 7 on ubuntu 19.10 ?

---

### Post by EuclideanCoffee on 2020-02-12
This is where you can install Java 7.

[https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html](https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html)

Unfortunately, you may find this method difficult.

Here is the package for VLC. Would this work?

[https://packages.ubuntu.com/search?keywords=vlc](https://packages.ubuntu.com/search?keywords=vlc)

Java does not appear to be a dependency here.

---

### Post by Holger_Gehrke on 2020-02-12
Blue Ray on Linux is a major hassle because of the DRM used on these discs. The movie files are encrypted and the maker of a player has to pay a license fee and sign a Non-Disclosure Agreement to get a key. NDAs and open source go together like oil and water and so there's basically no player on Linux that can play Blue Ray without using methods which might be legally questionable depending on the laws in your place of residence. A discussion of the methods that work(ed) can be found at [askubuntu]("https://askubuntu.com/questions/565516/can-linux-play-blu-rays").

Holger

---

### Post by mastablasta on 2020-02-13
why do you need java 7? why not java 11?

---

### Post by anje2 on 2020-02-13
> **ruze said:**
> This is where you can install Java 7.

[https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html](https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html)

Unfortunately, you may find this method difficult.

Here is the package for VLC. Would this work?

[https://packages.ubuntu.com/search?keywords=vlc](https://packages.ubuntu.com/search?keywords=vlc)

Java does not appear to be a dependency here.

I want the step how to install it

---

### Post by anje2 on 2020-02-13
> **Holger_Gehrke said:**
> Blue Ray on Linux is a major hassle because of the DRM used on these discs. The movie files are encrypted and the maker of a player has to pay a license fee and sign a Non-Disclosure Agreement to get a key. NDAs and open source go together like oil and water and so there's basically no player on Linux that can play Blue Ray without using methods which might be legally questionable depending on the laws in your place of residence. A discussion of the methods that work(ed) can be found at [askubuntu]("https://askubuntu.com/questions/565516/can-linux-play-blu-rays").

Holger

well , I have complete copy of bluray movie and I do play it on ubuntu using VLC player , but the problem is I can't use ( menu ) when the movie starts . it's ask download java to use menu or else just play the movie . so that I need java

---

### Post by anje2 on 2020-02-13
> **mastablasta said:**
> why do you need java 7? why not java 11?

java 11 and earlier version , dosnt work on ubuntu , that what i I know

---

### Post by mastablasta on 2020-02-13
java is (as far as i know) backwards compatible. here is how you can install java 11: [http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/](http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/)

there are also instances of old portable java floating around internet.

---

### Post by anje2 on 2020-02-13
> **mastablasta said:**
> java is (as far as i know) backwards compatible. here is how you can install java 11: [http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/](http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/)

there are also instances of old portable java floating around internet.

I have tried those steps but VLC player keep telling me ( you need to install java in order to play full disc bluray ) 
note / I can play bluray disc in vlc but I can't see menu bar , to show it on vlc I need to use java .
note / menu bar I mean ( play movie , choose subtitle , extra , ... )

check out attachment file

---

### Post by Holger_Gehrke on 2020-02-13
Two thoughts:

 
[LIST=1]
[*]Blue Ray players usually don't come with Java SE (Standard Edition) but with Java ME (Micro Edition). The ME not only leaves out a lot of features of the SE but also has - depending on the profile implemented - classes which are not part of the SE. 
[*]Is the vlc you are using a snap-package ? In that case snap-confinement might stand in the way of vlc seeing your Java. 
[/LIST]
 
Holger

---

### Post by anje2 on 2020-02-13
> **Holger_Gehrke said:**
> Two thoughts:

 
[LIST=1]
[*]Blue Ray players usually don't come with Java SE (Standard Edition) but with Java ME (Micro Edition). The ME not only leaves out a lot of features of the SE but also has - depending on the profile implemented - classes which are not part of the SE.
[*]Is the vlc you are using a snap-package ? In that case snap-confinement might stand in the way of vlc seeing your Java.
[/LIST]
 
Holger

sorry am a new ubuntu user ,what is snap -conf ?

---

### Post by Holger_Gehrke on 2020-02-13
snap is a new(-ish) package format. Programs installed as snaps are confined using apparmor-profiles. This stops them from accessing any part of the system that's not explicitly allowed to them. The profiles is stored inside the package, so you can't change it. If you installed vlc using the 'Software'-application it's quite likely that you installed a snap. To check enter 'snap list' in a terminal. This will list all installed snap packages.

Holger

---

