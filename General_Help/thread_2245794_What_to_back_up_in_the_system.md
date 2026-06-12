---
title: "What to back up in the system"
date: 2014-09-26
forum: General Help
---

### Post by Robbyx on 2014-09-26
I back up in prepartion for a fresh install:

Full markings
/Apt
fstab

what else should I be backing up so that I can bring back a fully repaired  system? Home is in a seperate partion so I am not asking about home backup. 

For example 
what about printer drivers and printer settings?
network settings?


R

---

### Post by whitesmith on 2014-09-26
I don't quite understand why or how you would backup printer drivers. They are part of the kernel in Linux.

What I do is generate a list of all installed programs with```
dpkg --get-selections > ~/my-packages   #save to usb or whatever
```
With the new OS installed I can bring it all back with ```
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
```

There's a zillion ways of handling this stuff, so others will have different ideas and goals. To me, being able to get back to where I was with installed applications is No. 1.

---

### Post by Robbyx on 2014-09-26
You are doing the same as me except I find it preferable to use synaptic and its markings.

The extras:

The printer drivers are drivers I have to install seperately and it would be preferable to just copy them back from a backup. Same applies to the scanner and the various network settings I use. Is there a way to do this?

R

---

### Post by Michael_McKenney on 2014-09-26
I backup data, www folder with my web site, *.conf files I manually configure, and anything I manually have to configure elsewhere.   I am installing Bacula on my workstation to be able to backup to my tape drives.  It does allow DVD drives to.  You can even schedule backups on it.

---

### Post by whitesmith on 2014-09-26
> **Robbyx said:**
> You are doing the same as me except I find it preferable to use synaptic and its markings.

The extras:

The printer drivers are drivers I have to install seperately and it would be preferable to just copy them back from a backup. Same applies to the scanner and the various network settings I use. Is there a way to do this?

R

What kind of printer do you have? A further question: Yours is an all-Linux box, correct?

---

### Post by Robbyx on 2014-09-26
I use the Brother MFC 5460cn. It is a combined printer and scanner. On a  fresh install the drivers will not be supplied with Ubuntu so I have to  install  Brother's drivers, even though they go through cups.

The machine is purely UbuntuGnome 14.04 although I do use VirtualBox to run abbyy's OCR software in windows. 

R

---

### Post by whitesmith on 2014-09-26
OK. Now your post makes sense. This is the path I took: I asked myself how much time it would take to restore changes wiped out by a bare-metal upgrade. When the total of manual changes reached an  hour, I made a backup of the necessary settings. In other words I can go from bare metal to a fully functioning system in 1 hour plus installation time for the OS. Regards.

---

### Post by Robbyx on 2014-09-26
I assume the I can ignore the settings stored in Home, but I will need to copy over some of the directories in the system area. I have taken that attitude with copying all of apt, but what should I copy for the printer drivers that  I install  and where can I find the network profiles?

---

### Post by whitesmith on 2014-09-26
Try /etc/NetworkManager/system-connections

---

