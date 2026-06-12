---
title: "hda1 in Ubuntu/Kubuntu"
date: 2007-09-30
forum: General Help
---

### Post by Rob500 on 2007-09-30
I know there is probably a very simple explanation for this, but I'm stumped about it.

When I boot from an Ubuntu live CD, it recognises hda1 and displays it in Places > Computer. I can then access files on it as per usual.

Thing is, when I boot using a Kubuntu live CD, hda1 is not recognised anywhere. Is there a simple explanation for this?

Many Thanks :)

---

### Post by kellemes on 2007-09-30
Well, it is not mounted in Kubuntu it seems.. has nothing to do with recognition.
Yo have to do this using "mount" if you need it.

---

### Post by Rob500 on 2007-09-30
Hmm, I found them in /dev/ but I don't seem to have permission to access them :confused:

---

### Post by ajgreeny on 2007-09-30
Using Kubuntu live open a terminal and type ```
sudo mkdir /media/hda1
``` to make a folder as a mount point.  Now type ```
sudo mount /dev/hda1 /media/hda1 -t ext3
``` and this should mount the disk and allow you to see files on it.

---

### Post by Rob500 on 2007-09-30
```

ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/hda1 -t ext3
mount: special device /dev/hda1 does not exist

```

I just get this if I try that :confused:

I'm only using the live CD but surely that shouldn't make a difference.

```

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Then this after trying sda1 instead of hda1

Jeez everything works fine on Ubuntu, why is Kubuntu like this?

---

### Post by Rob500 on 2007-09-30
*bump*

---

### Post by ajgreeny on 2007-09-30
What is the output of ```
sudo fdsik -l
``` in terminal of the kubuntu liveCD?  Perhaps kubuntu is not seeing the disk as hda1 or sda1 for some reason.

---

