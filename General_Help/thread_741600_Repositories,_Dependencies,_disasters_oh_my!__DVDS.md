---
title: "Repositories, Dependencies, disasters oh my!  DVDStyler"
date: 2008-03-31
forum: General Help
---

### Post by bobbo85 on 2008-03-31
I tried installing "DVDStyler 1.6.1"  today after seeing the headline on GnomeFiles.org.

 I guess the bottom line is that I have these questions:
1)  Which repositories should I have to get the latest stable releases of software?
2)  What is difference between debian and ubuntu, and why do the repositories seem to conflict?
3)  What was that partial upgrade?  Did I break anything?
and of course
4)  How can I get this program to install?!!!


The problem:  After adding some different repositories, the system updater kept on asking me to update things, then somehow it ended up "breaking" dependencies.  I ran a command to fix the broken dependencies, but I am still lost, frustrated, and have not installed the program!

What really freaked me out was at one point it said "can't install all updates, do you want to do a partial update?" and it said something about updating my distribution.  Things seem fine, although it installed a bunch of new programs like iceape, which i removed afterwards.  Could someone explain to me what that partial update was?



My approach was this:
Use a terminal, navigate to the source folder, type ./configure
Read the error at the bottom, check synaptics for whatever it asks for - example "mjpegtools."
google whatever I can't find in synaptic (mjpegtools for example)

This lead me to several sites that claimed that adding repositories x,y,z would allow me to use synaptic to install the program and handle the dependencies.

I tried adding in the following repositories:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main
deb [http://dvdstyler.sourceforge.net/repository/debian/](http://dvdstyler.sourceforge.net/repository/debian/) testing main
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) breezy main (Changed "breezy to ubuntu" but it didn't work)

The next thing I found was that [http://dvdstyler.sourceforge.net/downloads.html](http://dvdstyler.sourceforge.net/downloads.html) has 2 deb packages to download.  I installed the second one, then tried to install the main DVDStyler one...
This said mjpegtools was unsatisfiable... I installed it myself from one of those new repositories using synaptic... but the deb still says that it is unsatisfiable!


Thanks in advance!  Oh and if it helps, I can post my synaptic history entries in another post - I installed/upgraded/removed a lot of stuff today, I hope I didn't break any of it!

---

### Post by zvacet on 2008-04-02
```
gksudo gedit /etc/apt/sources.list
```

remove every line which is not **gutsy** related (exept of medibuntu).Save file and then close it.In terminal type

```
sudo apt-get update
```

Go to the system>admin>software sources>check all boxes under Ubuntu software and updates tab.Reload.Now you will find mjpegtools in synaptic.You can download latest DVDStyler [here.](http://www.getdeb.net/search.php?keywords=DVDStyler)

---

### Post by kpkeerthi on 2008-04-02
Your sources.list file looks messy. You seem to have incompatible sources in it and thats why you ended up with a broken dependency. When you are using gutsy, use only gutsy repositories. Do not use Debian's or Breezy's. 

Use [this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories") and do ```
sudo aptitude update && sudo aptitude dist-upgrade
``` and lets hope the breakage is fixed.

---

