---
title: "Downloadable from the Internet"
date: 2008-06-08
forum: General Help
---

### Post by :overclock: on 2008-06-08
Hi, I'm new here and don't know if I posted this in the right section but anyway, here's what I'm asking:

I'm about to install Compiz Fusion but after all the terminal stuff, when I wanted to install it, at the add/remove window it says: "**Desktop Effects cannot be installed on your computer type (i386)**

Either the application requires special hardware features or the vendor decided to not support your computer type."

But I found in this forum a post reply that solved the problem: "*I had the same problem when using 7.10 and fixed it by clicking on the "Preferences" button in the lower left of the "Add/Remove Applications" window and enabling all the "Downloadable from the Internet" sources.*"

BUT, I don't find any preferences button here (I'm using Ubuntu 8.04). This may be a very n00by question but I really can't find an answer :(

---

### Post by RadarBat on 2008-06-08
What kind of computer do you have?

---

### Post by :overclock: on 2008-06-08
32bit :(

2.8GHz Intel Pentium D
2 x 1024 MB RAM
Nvidia GeForce 8600GT 512MB

(don't know what else to write when speaking of performance...)

I know it's just for 64bit (as far as I understood it) but the post that I saw here solved the problem... or didn't it :S

---

### Post by RadarBat on 2008-06-08
I could not find a way to run visual effects on my 32-bit machine, but I can on a 64-bit gamer.

---

### Post by :overclock: on 2008-06-08
Ohh.... Hope someone knows... I have to go to sleep cause it's 4 AM here (I stuck in my PC because of this problem).

I would appreciate if somebody finds an answer to my problem.

---

### Post by ravenvii on 2008-06-08
Compiz Fusion is included in 8.04 already, you don't have to install it. Simply go to System > Preferences > Appearance, and click the Visual Effects tab. If you can change the effects to "Normal" or that other option, you're golden. If you can't change it from none, then you either: have to install drivers for your video card, or your video card is blacklisted (see the Blacklisted? sticky for more details).

---

### Post by :overclock: on 2008-06-09
My graphics card driver is enabled and I'm using the "extra" visual settings but it isn't the same like with compiz (all the 3D box desktops, 4 desktops etc.). 
I've been trying to find a solution and saw in a website that you can install Compiz Fusion with Synaptic Package Manager but it says to activate these two:     * compizconfig-settings-manager * eremerald

I don't have any of these two. I only have (from the compiz ones):
compiz
compizconfig-backend-gconf
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins

---

### Post by Forlong on 2008-06-09
What's the output when trying to install ccsm via the terminal:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by :overclock: on 2008-06-09
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

---

### Post by Forlong on 2008-06-09
Please post the content of your /etc/apt/sources.list

---

### Post by :overclock: on 2008-06-09
For some reason it says permission denied, even in root@....

---

### Post by Forlong on 2008-06-09
It's a text file. Just run your favourite text editor and open it in there. Then copy & paste the content here.

---

### Post by :overclock: on 2008-06-09
hehe it's been 2 days since I've started with ubuntu...

Here:
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse

---

### Post by Forlong on 2008-06-09
Oh, did you really install Breezy?
That is almost 3 years old.

Can you please run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)


edit: but was that really the whole content of that file?

---

### Post by :overclock: on 2008-06-09
Replied in the Compiz-Check -- no more "Desktop effects could not be enabled" topic.

---

