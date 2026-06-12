---
title: "shortcuts to folders?"
date: 2014-02-21
forum: General Help
---

### Post by hotshot247 on 2014-02-21
hey, I was just wondering..I am dualbooting windows 7 and ubuntu 13.10 and i have to access my windows partition to get certain files but what i was wanting to know is that is their a way to take the My Videos folder in windows and make shortcuts in the Videos folder where the Videos in windows will show up in the videos folder in linux? just so when i go to the videos folder in linux, the videos from windows and linux will show up in there. Thanks!

---

### Post by IvoGuerreiro on 2014-02-21
Hi, Hotshot247 
One suggestion you can create a 3th partition, and labeled as internet stuff.
formatted in NTFS.
Now you just to use that partition to your movies.

---

### Post by hotshot247 on 2014-02-21
yea, that's a good idea. I think i'll try that out and see how i like it. Thanks!

---

### Post by monkeybrain20122 on 2014-02-21
You need to do two things:
 1) mount the external partition automatically and 2) create a shortcut launcher to the folder in the partition.

For 1) In the dash, type "disk" to bring up the disk utility, then locate the partition you want to automount at start up, go to the double gear menu in the bottom of the partition layout (not the one on top, see screenshot), choose "Edit Mount Options" and turn off "automatic mount options" and it will automatically mount when you reboot. You can also edit fstab but this is simple

For 2) see [http://ubuntuforums.org/showthread.php?t=2200963](http://ubuntuforums.org/showthread.php?t=2200963)

---

