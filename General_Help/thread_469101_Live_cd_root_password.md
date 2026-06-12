---
title: "Live cd root password?"
date: 2007-06-09
forum: General Help
---

### Post by hooksie on 2007-06-09
Hey there,

XP just blue screened and completely corrupted itself (hooray windows *sigh*), so I decided to use my ubuntu live-cd to back up some files before formatting into a Windows/Ubuntu dual boot.

Problem being, when I go to use sudo (or su) it wants the root password, and I don't know what it is.

Can anyone tell me what it is?

Thanks.

---

### Post by thelinuxguy on 2007-06-09
Even I don't know what the default password is but this worked for me on the livecd:

Goto System >> administration >> Users and groups (doesn't ask for password)
Select the user >> properties >> set password by hand

---

### Post by hooksie on 2007-06-09
Thanks a bunch.

Second question, why cant I create new directories from the live CD?

---

### Post by thelinuxguy on 2007-06-09
If your windows partitions are NTFS formatted, they are mounted read-only. Which Live CD are you using? Can't say about Feisty but till Edgy, the live cd mounts NTFS partitions this way. If you got the Live CD delivered to you for free, then you don't have Feisty. You have to install ntfs-3g to gain write access to your NTFS drives. Haven't done this from the Live CD though.

Edit: Just checked and they are shipping Feisty free of charge. I was under the impression that this will be available once Gutsy is out.

---

### Post by hooksie on 2007-06-09
Yeah, I'm using one of the gettit live CDs of feisty.

Do you see any problems with installing ntfs-3g running off the live-cd?

---

### Post by thelinuxguy on 2007-06-09
I don't see any problems but can't be sure since I haven't done it myself. Also you are trying a data backup so I wouldn't recommend any experiments.

---

### Post by hooksie on 2007-06-09
Well, the thing is, all my paritions are NTFS, and aside from doing a repair install of XP (which seems to be what I'll most likely do at this point), theres no way for me to get into windows.  Still, repair installs arn't perfectly safe for data (at least not to my knowledge).

Also, the following command

sudo apt-get install ntfs-3g

tells me the package wasn't found.

Any ideas on how I could back things up besides what I've said here?


Additionally, I'm not all too worried.  All my really important files (papers for school, music, etc) were kept on seperate partitions.  Those are safe.  The few important files left on my windows partitions (a few work files) should have all been backup up hourly to remote servers through Mozy back when windows was still working right.  There were a few configuration files that I had wanted to preserve, mainly, and for peace of mind, re-back up the files Mozy should have, thats all.

---

### Post by thelinuxguy on 2007-06-09
Take a look here: [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

Also, look at response #4 and #41 on that page. If your data is safe, I guess it wont hurt to try.

---

### Post by hooksie on 2007-06-09
Alright, thanks a bunch for your help.

---

### Post by thelinuxguy on 2007-06-09
> **hooksie said:**
> Alright, thanks a bunch for your help.

You are welcome. Do post back with your progress.

---

### Post by merlinus on 2007-06-09
> 
Also, the following command

sudo apt-get install ntfs-3g


Try 

sudo apt-get install ntfs-config

-merlin

---

