---
title: "Ubuntu total reinstall"
date: 2008-05-17
forum: General Help
---

### Post by thepieguy on 2008-05-17
My Ubuntu 7.10 is way, way messed up. I messed it up myself and I was wondering if I could totally reinstall. would running the live CD and installing to my current partition work? Also, would upgrading to 8.04 via the cd work either?

---

### Post by ibuclaw on 2008-05-17
Yes, it should first most things!

But first, backup all your precious files, as your partition will be re-formatted.

If you choose to re-install gutsy, you can recover all your currently installed programs via this command:
```
dpkg -l | grep ii | awk '{print $2" "}' | tr -d '\n' >~/packages.lst
```
And when you reinstall gutsy, cd to the location of the file and type in:
```
sudo apt-get install `cat packages.lst`
```

Hardy is a good option too. It's always good to stay ontop of those security fixes and keep your desktop secure.

Though, if you don't want to download the iso image, you can always upgrade to it after you re-install gutsy:
```
sudo update-manager -d
```
And follow the on-screen instructions.

Regards
Iain

---

### Post by bodhi.zazen on 2008-05-17
Depends on what the nature of the problem.

If you re-install, the installation process will format the HD and return you to the defaults.

Unless you have a separate /home or /data partition you will lose your data, so back up first.

---

### Post by thepieguy on 2008-05-17
I have vista with VERY precious data on another partition. my disk is configured as so:
a 47 mb partition (EISA configuration) ...?
a 10 gb dell recovery partition
a 47.65 gb windows vista partition
a 14.16 gb ubuntu partition
a 682 mb partition. (swap?)
a 2 gb partition (ext3 so I guess it's ubuntu related)

will it wipe my ubuntu partitions only?

---

### Post by bodhi.zazen on 2008-05-17
It will wipe what you tell it to. Use manual partitioning and be sure you understand teh "format" box and what partitions you want to format.

---

### Post by Sef on 2008-05-17
> Unless you have a separate /home or /data partition you will lose your data, so back up first.

Even if you have a separate /home or /data partition, you should **back up** your data, you don't want to make a mistake and lose your data without having a back up.

---

### Post by thepieguy on 2008-05-19
I now have hardy heron on a disc. If I specify that I want these partitions formatted, will it do as I say? Then can I install peacefully?

---

### Post by Cap'n Skyler on 2008-05-19
> **thepieguy said:**
> I now have hardy heron on a disc. If I specify that I want these partitions formatted, will it do as I say? Then can I install peacefully?

just be SURE of your choices and if you dont fully understand it,stop and go find the info you need to figure it out.:)

---

