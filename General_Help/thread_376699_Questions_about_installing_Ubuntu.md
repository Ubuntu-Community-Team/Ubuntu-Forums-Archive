---
title: "Questions about installing Ubuntu"
date: 2007-03-05
forum: General Help
---

### Post by sweetboi on 2007-03-05
hi everyone i am new here and also new to using linux so i am asking these question before i proceed to install ubuntu.

i have windows xp installed already on a partition i have a next partition which is 32.37 GB i was just wondering if i install ubuntu on the 32.37 GB partition will it affect windows xp home edition which is already installed?

whats the difference between Ubuntu, Kubuntu, Edubuntu and Xubuntu. ?

---

### Post by rjfioravanti on 2007-03-05
if you have one partition that uses windows, and install ubuntu into another partition, then XP will be untouched. Your second partition will be split up into two different partitions however (type ext3 is the typical linux filesystem it will format it to), it needs two, one for just regular, and another as a swap partition. This swap parition is supposed to be twice the size of your computers RAM

Ubuntu installer will put GRUB onto your computer, which will allow you to choose at start time which OS to boot. 

Ubuntu uses GNOME desktop, Kubuntu uses KDE

Edubuntu is for education or something and I'm not too sure what Xubuntu if for, but theres lots about that on the ununtu site

Also if you are interested, just google ext, swap paritition, GRUB, GNOME, KDE; for more information about your questions (search them one at a time =) )

---

### Post by Bloch on 2007-03-05
You might like to start with standard ubuntu (unless you are the adventurous type) for the simple reason that when you ask questions on the forum more people can help you.

If you've been doing your reading you'll know the biggest challenge after installation is to get the proprietary stuff working - flash plugin, windows codecs, realplayer, DVD-playing ability, and your graphics card driver if you have a separate graphics card.

Automatix can help you with these (look it up on google). 

Good luck

---

### Post by ofek on 2007-03-05
Xubuntu uses xfce as its windows manager and it is quite faster and more light weight than kde and gnome. 
About the swap partition if u have more than 1G of ram don't use a 2G swap partition it's just 2 much 512 should be enough for any normal use, the rules of the UrRam*2 are obsolete and refer to the times when no one had more than 256 ram but huge server.

---

### Post by sweetboi on 2007-03-05
soo all i need to do is burn the iso images onto a cd, boot it and it will guide me through the  steps of how to install it ?

---

