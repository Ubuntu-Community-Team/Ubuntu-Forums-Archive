---
title: "Downloading from FTP"
date: 2004-11-08
forum: General Help
---

### Post by Slapdash on 2004-11-08
OK , Linux uses dependencies.

So in other words if I download a .DEB package and I use dpkg to install it's not a given that its gonna work because of the dependencies.

No I download said dependencie and everything - -Where do I put it? / install ?
What do I do with that dependency?

Also how can I see what dependencies I already have installed using this method instead of Apt-get?

---

### Post by ulrich on 2004-11-08
sounds really psychedelic your question... :D

if youre trying to install an debfile which has depencies, i hope you downloaded the defiles which contain the files to solve the dependency. so you then install that deb with dpkg. like the origin package that you were trying to install.

but are you completely sure, you have to download this debfile and you're sure this pakckage isnt in universe or multiverse!?

have you checked [http://www.ubuntulinux.org/wiki/SynapticHowto](http://www.ubuntulinux.org/wiki/SynapticHowto) ?
this a graphical tool for installing/removing packages that comes with ubuntu.

---

### Post by Slapdash on 2004-11-08
hehehe yeah it does  sound a bit "off the wall" ;)

I'm really trying to get  around all the nuances of Linux and it makes for interesting topics ( i feel like such a NOOB!! )  I've been into Dos and Windows since 3.1 I code ASP, a little PHP ( going to try broaden this a lot ) and VB etc. for me to come to Linux and knowing NOTHING is quite an experience ( one I like but it can be frustrating  :mrgreen:  )   

Anyway, yeah the Synaptic thing looks great only that I wont have a internet connection to from my house for a while ( I'm renting currently while my Appartment is being built  - Will only be finished somewhere  July  :(   )  
anyway so I have a FTP connection set up here at work with ALL the DEB files one could ever want ( i think ) and I want to download some 3D engines to work on so I can start seeing what gaming possibilities I have for Linux 

Been making games for windows etc. but Linux could really use more Games , hence my interest.

Anyway, the FTP and.Deb packages etc looks like this for instance:


totem-xine_0.99.20-2_i386.deb
totem-xine_0.99.16-2_arm.deb
totem-gstreamer_0.99.20-2_i386.deb
totem-gstreamer_0.99.16-2_sparc.deb
totem-gstreamer_0.99.16-2_alpha.deb
totem_0.99.20-2_all.deb
totem_0.99.20-2.diff.gz
totem_0.99.20-2.dsc


So what do I download 
totem-xine_0.99.20-2_i386.deb  I figure is for my proccessor Athlon XP 2600+
but what about all the other files + dependencies?

---

### Post by ulrich on 2004-11-08
godd thing! more 3d for linux isnt the badest idea someone can have! ;)

for the files you list:

totem-xine_0.99.20-2_i386.deb **< may be the deb you want!**
totem-xine_0.99.16-2_arm.deb **< the deb you really dont want; its for arm-processors**
totem-gstreamer_0.99.20-2_i386.deb **< may be the deb you want!**
totem-gstreamer_0.99.16-2_sparc.deb **< the deb you really dont want; its for sparc-processors**
totem-gstreamer_0.99.16-2_alpha.deb **< the deb you really dont want; its for alpha-processors**
totem_0.99.20-2_all.deb **< i dont know :)**
totem_0.99.20-2.diff.gz **< a patchfile!? (may be used if you build your own pakcages)**
totem_0.99.20-2.dsc **< should be description!?**

mostly you go for the i386-packages > your cpu-architecture i assume.

and mostly you just have to download the .debs you want, burn them on cd, mount the cd, open a terminal, cd in the apropriate folder and firing up **dpkg -i *.deb**

---

### Post by Julius on 2004-11-08
Correct me if I'm wrong, but I think totem-gstreamer and totem-xine cannot be installed at the same time (in Synaptic, if you check one for installation the other one, if installed, will be check for uninstallation)

---

### Post by ulrich on 2004-11-08
no youre right.
i for myself use mplayer so i hadnt thought about that in the first line...

---

