---
title: "Check for errors"
date: 2012-10-17
forum: General Help
---

### Post by Deucalion29710 on 2012-10-17
Morbid curiousity...Is there a Linux program that is similar to Microsoft's Scandisk or Checkdisk that scans for, identifies, and fixes system errors?

---

### Post by jerrrys on 2012-10-17
There is Disk Utility.  Not sure if its preloaded in xubuntu or not.

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

---

### Post by CharlesA on 2012-10-17
fsck will scan the drive for file system errors.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
[LIST=1]
[*][Gparted](apt:gparted)
[*][Disk Utility](apt:gnome-disk-utility)
[/LIST]

---

### Post by Deucalion29710 on 2012-10-17
I have tried Synaptic Package Manager, but it might as well be written in Swahili.  I don't understand how to use it at all.   Is there anything that automatically scans and fixes in a similar fashion as Check Disk?  I do have GParted, so I may look at my options there.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
what kind of issue do you suspect?
damaged data? incorrectly install program? missing dependency?

---

### Post by Deucalion29710 on 2012-10-17
At first I was seeing "internal 12.04 LTS error" quite a bit.  I havent seen the same error in a couple of days.  I would also like to assure that all dependencies are met.

---

### Post by jerrrys on 2012-10-17
> **Deucalion29710 said:**
> I would also like to assure that all dependencies are met.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

If anything bad is going on this will give you errors.

Edit:  You may also be interested in [maintenance commands]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands").
[B]
[/B]

---

### Post by Deucalion29710 on 2012-10-17
> **jerrrys said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

If anything bad is going on this will give you errors.


Thank you very much.  No reported errors, so I think it's alright.

---

### Post by jerrrys on 2012-10-17
Welcome  :) and synaptic is basically a GUI for apt-get.

---

### Post by otetiani on 2012-10-17
I like the built-in tune2fs that runs e2fsck on a scheduled bases.  Just found out it was disabled by default on 12.04 though so you have to enable it here is how:  [http://ubuntuforums.org/showthread.php?t=2072400]("http://ubuntuforums.org/showthread.php?t=2072400")

it should check your all of your Ubuntu partitions, except swap of course.

type ```
$ mount
``` to see what is mounted

---

