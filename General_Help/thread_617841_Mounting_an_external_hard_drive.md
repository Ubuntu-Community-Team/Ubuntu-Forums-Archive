---
title: "Mounting an external hard drive"
date: 2007-11-19
forum: General Help
---

### Post by AppleCyder on 2007-11-19
Just installed ubuntu today and wow, I'm confused... I'm a total linux noob by the way. I have an external hard drive which shows up in 'computer' but when I click on it, it says "cannot mount volume". I looked around the forums a bit and tried a few things like mount /dev/sdb but in all honest I don't have a clue what I'm doing.

Can some explain in a step-by-step order how I can get this drive to work??? It's a Maxtor 250GB NTFS hard drive.

---

### Post by taurus on 2007-11-19
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by AppleCyder on 2007-11-19
Thank you so much taurus. That's exactly the kind of straight forward answer I was looking for. Just out of curiosity, what exactly does all of that code mean? What is 'sudo' and 'ls' and 'la'??

---

### Post by sonofusion82 on 2007-11-19
you can easiy google for "linux command reference" when it comes to linux commands

here's a nice quick reference to print out:
[http://people.debian.org/~debacle/refcard/](http://people.debian.org/~debacle/refcard/)

---

### Post by sonofusion82 on 2007-11-20
you can easiy google for "linux command reference" when it comes to linux commands

here's a nice quick reference to print out:
[http://people.debian.org/~debacle/refcard/](http://people.debian.org/~debacle/refcard/)

---

### Post by adrock1942 on 2008-04-26
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```
this worked very well, thank you. However, i have to do this every time i restart my computer. Is there a permanent way to mount an external hard drive?

---

### Post by vanadium on 2008-04-26
I am very much surprised about the advise you got. These commands would have been necessary in Ubuntu 7.04, that did not by default supported writing to ntfs drives.

By default, external hard drives in Ubuntu mount automatically with full rights for the current user. If yours does not, then it indicates a problem with your drive.

A common issue with ntfs drives is that the drive was not properly closed by Windows. This happens for example when you hibernate Windows, then disconnect the drive. It may also happen when disconnecting the drive while it is in use.

To solve such issue with an ntfs volume, you unfortunately need Windows (again): load Windows, connect the drive and then shut down Windows completely. It might be necessary to restart and shut down Windows a second time, with the drive connected. After that, the drive should automatically mount in Ubuntu.

---

### Post by jonathan451 on 2008-05-14
I need help i have a Dell latitude 120l and i am trying to mount my external hard drive... i bought a encloser for a internal hard drive the encloser name a dynex i need some help ppl plz... i cant mount it on Ubuntu the hard drive is a seagate barracuda 7200.8 250 gb ubuntu v8.0 +

---

### Post by Cannonzim on 2008-07-23
I tried everything here, but  it still wont mount

any suggestions?

---

