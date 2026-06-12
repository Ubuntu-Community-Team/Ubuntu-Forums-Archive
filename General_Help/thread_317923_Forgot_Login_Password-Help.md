---
title: "Forgot Login Password-Help"
date: 2006-12-13
forum: General Help
---

### Post by dontgetshocked on 2006-12-13
I managed to mistype my password and apparently didnt pay attention.
How can I get back in?
I can login as 1 normal user but with no root privileges

Save me from myself, Please


Thanks,

---

### Post by engineer on 2006-12-13
boot with a live cd, mount the main partition of your linux installation

chroot to the directory, where you mounted the partition of your harddisk

```
chroot /dir /bin/bash
```

update the password with the passwd [username] command

eg:
```
passwd homer
```

---

### Post by taurus on 2006-12-13
Or boot into recovery mode from GRUB menu and at the prompt, change the password for that user, **john** (assuming john is the username...)!

```
passwd **john**
```

---

### Post by namelessone on 2006-12-13
Also, when grub starts up, you can press "e" to enter edit mode, and edit one of the lines by adding the word "single" onto the end. Then press "b" to boot into linux single mode, which will give you root privileges. From there just type ```
passwd username
``` to change your password.

---

### Post by PetePete on 2006-12-13
i wasn't aware of these methods..

isn't this quite insecure? i mean anyone could access my account and data if they have pyhsical access to my PC ?

its almost as bad as windows :o

---

### Post by taurus on 2006-12-13
If I have an access to your computer, I can use the LiveCD and wipe out your harddrive if I want it to even if I don't know your root's password!!!  Therefore, don't let people you don't know to have physical access to your machine and if you look at those big corporates, they have their machines log up in a secure room and only a few trusted people who have access to that room...

---

### Post by PetePete on 2006-12-13
yes, well theres one thing wiping the HDD, and another stealing information and no one noticing

i mean in windows, its relativly secure as long as you have a password on your admin account , i know theres boot CDs to wipe the passwords but this requires 3rd party tools. in linux it seems that anyone can use the settings there to remove passwords :S

---

### Post by taurus on 2006-12-13
I can steal important files from your XP even if I don't know your admin password for it.  All I need is a LiveCD and physical access to your computer...  I can even wipe out the whole entire harddrive, reformatting it with the LiveCD!

---

### Post by namelessone on 2006-12-14
The number one rule of all computers:

If a hacker can touch your machine, it is no longer your machine.

This is actually more like a rule for technology in general.

Even if you change the boot order in CMOS to put the harddrive first instead of cdrom or floppy and set a CMOS password, a hacker can physically open up your machine and take out the onboard battery, resetting the CMOS settings to default.

Virtually nothing is more secure than a physical lock and key.

---

### Post by mcduck on 2006-12-14
Only way to make your files even fairly secure if somebody ca get physical access to the machine is encrypting everything. And even that only makes opening them slower. No matter what OS you are running.

So if you are worried about your files make sure nobody can access the machine :)

(you can also set a password for Grub, making access to your machine a bit harder. but that only stops those who don't know how to move your hard drive to another machine or boot a live-cd)

---

### Post by tragicglee on 2006-12-14
> **PetePete said:**
> i mean in windows, its relativly secure as long as you have a password on your admin account , i know theres boot CDs to wipe the passwords *but this requires 3rd party tools*. in linux it seems that anyone can use the settings there to remove passwords :S

3rd party tools *aren't* required to gain admin rights on a win box by any means. 2K and XP are the only OSes I can speak about with certainty, but I can't imagine this _not_ applying to  2003 and Vista, as well :-? 

Windows ships with *Microsoft's* Recovery Console, which can be run from the OS's install CD, assorted bootable media, AND the *hard drive* - if someone opted to install it (if its there, you'll find it in mode options accessed with F8). Recovery Console allows for full control of a machine, no password required :P 

Granted, it only allows CLI usage ((not that thats a drawback)) and *is* fairly limited in what it can do - but the information theft you bring up doesnt seem difficult at all.

---

