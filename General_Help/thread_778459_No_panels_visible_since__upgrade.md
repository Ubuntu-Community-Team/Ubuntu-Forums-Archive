---
title: "No panels visible since  upgrade"
date: 2008-05-02
forum: General Help
---

### Post by FrancesL on 2008-05-02
Hi
I don't exactly know what is the issue, but after 'panic' posts and then today having another look, I find that i actually have a system, i thought I had trashed something..but no panels, that I can access,,,so no access to applications etc..I am using a web page I had saved to desktop folder to launch FF. My right click Launch Application inst working, nor is <Alt-F2> to launch a terminal window. To shut down I am using <Alt-Ctrl-Backspace> . I had a thought that maybe since updating to Hardy, my desktop resolution MAY, JUST may be set to such a size that it is obscuring the panels..other than that..I am at a loss. Your thoughts and suggestions are invited and welcome.

---

### Post by TeoBigusGeekus on 2008-05-02
Boot into recovery mode and type
```
sudo dkpg-reconfigure -phigh xserver-xorg
```
to reconfigure your graphical settings.

---

### Post by FrancesL on 2008-05-02
> **TeoBigusGeekus said:**
> Boot into recovery mode and type
```
sudo dkpg-reconfigure -phigh xserver-xorg
```
to reconfigure your graphical settings.
 Tried this and got xserver is not installed

---

### Post by MongooseCage on 2008-05-02
If you don't mind formatting, use a Live Disc, Save everything and install it again.

Or maybe create a launcher for the panels or something, just hoping to spark something.

---

### Post by TeoBigusGeekus on 2008-05-02
Ok, type
```
sudo apt-get install xserver-xorg
```

---

### Post by FrancesL on 2008-05-02
> **MongooseCage said:**
> If you don't mind formatting, use a Live Disc, Save everything and install it again.

Or maybe create a launcher for the panels or something, just hoping to spark something.

thanks for your thoughts, no, I dont mind formatting..I already saved to external hdd anything I needed prior to upgrade. I downloaded ISO and burned to CD following instructions on Ubuntu website..so do I just insert that and let it run..?

---

### Post by FrancesL on 2008-05-02
> **TeoBigusGeekus said:**
> Ok, type
```
sudo apt-get install xserver-xorg
```

Did that and returned 'xserver-xorg is already newest version'
 plus a list of packages with use 'apt-get autoremove' to remove them

---

### Post by TeoBigusGeekus on 2008-05-02
Could you post the whole output please?

---

### Post by FrancesL on 2008-05-02
> **TeoBigusGeekus said:**
> Could you post the whole output please? 
'x-server is already the newest version'
after sudo apt-get autoremove gnome-icon-theme-gartoon 
Removing libavahi-gobjecto
Removing libdata-googlee1.2.1 libgdata1.2-1 Removing linux-backports-modules-2.6.22-14-generic..update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic 
removing w3c-dtd-xhtml 
removing 
openjdk-6-jre-headless 
removing openjdk-6-jre-lib
removing libaccess-bridge-java
removing tzdatta-java
Processing triggers for libc6
Idconfig deferred processing now taking place

all happened by themselves 
after which I entered sudo apt-get install xserver-xorg again
got Reading package lists...Done
Building dependency tree
Reading state information...done
xserver-xorg is already the newest version




*I hope i copied all that correctly, did my best looking over my shoulder from old desktop..
I am grateful for you help. 
Is there any other thing you can suggest before I resort to Formatting using the CD?

---

### Post by TeoBigusGeekus on 2008-05-02
Try first
```
sudo dkpg-reconfigure -phigh xserver-xorg
```
again, and then format...

---

### Post by TeoBigusGeekus on 2008-05-02
Did it work?

---

### Post by FrancesL on 2008-05-03
sorry for taking so long to get back, we got hit by an electric storm and I had to close down..but did try the sudo dpkg etc again and no go...so will have to use cd to reformat and install, due to constrictions on my time, I have not got to it as yet. That will be tomorrow, Sunday my time, thanks again for your help. We gave it our best shot TeoBiggusGeekus!

---

