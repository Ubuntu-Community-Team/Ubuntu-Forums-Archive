---
title: "Increase size of filesystem root"
date: 2016-04-03
forum: General Help
---

### Post by Sebastian_Ulloa on 2016-04-03
Hello everybody,
I'm trying to increase the size of the filesystem root (dev/sda5) because it's full.
Mi partitions look like this

[IMG]http://s28.postimg.org/glv1ju331/Screenshot_from_2016_04_03_18_19_30.png[/IMG]

I tried to shrink the windows partition to increase /dev/sda4/ but I couldn't, then I do the same thing with /dev/sd6/ but it seems that the empty partition and the one I'm trying to increase should be side by side.
Please tell me there is any way to do it without losing my ubuntu data.

---

### Post by deadflowr on 2016-04-03
Right click on the swap partition and mark the swap off option.
Then it should work.

---

### Post by Sebastian_Ulloa on 2016-04-03
Does it damage ubuntu or something?

---

### Post by deadflowr on 2016-04-03
> **Sebastian_Ulloa said:**
> Does it damage ubuntu or something?
Turning off swap?
No
While swap is nice to have, it's not mandatory except for hibernation scenarios.
I doubt you'll be hibernating during the re-allocationing of the partition spaces, so no need to have it enabled.

---

### Post by yancek on 2016-04-03
You need to use the Ubuntu Live CD/flash drive which has GParted on it or you need to use a GParted CD.  You can't make those modifications from a running/mounted system.

> I tried to shrink the windows partition to increase /dev/sda4/ but I couldn't,

You can boot windows and shrink the partition sda3.  The problem with that is that sda4 is an Extended partition and you will have to turn swap off and unmount all the partitions sda5 and higher before you do anything.  Also, if you move sda5 into the unallocated space you create by shrinking windows, you will first have to move the Extended partition to the left.  You will then need to move sda5 to the left.  Since this is your / partition and has your boot files on it, you will also be moving them and your machine will not boot with Grub unless after the move, you immediately chroot and update grub.

> then I do the same thing with /dev/sd6/ but it seems that the empty  partition and the one I'm trying to increase should be side by side

There is no empty partition, you do have unallocated space.  The simplest solution would be to resize the home partition by moving it to the right to include the 15GB unallocated space.  I beleive you would then need to move the beginning of the /home partition to the right to leave unallocated space at the end of the / partition (sda5).  You could then resize that partition to enlarge it.

> Please tell me there is any way to do it without losing my ubuntu data. 		

Luck.  You will never get a guarantee of something like that with free software and I doubt even with software you pay for.
The problems are a result of poor choices, your / system partition is way too small.  A current Ubuntu basic install is over 6GB so if you never installed any new software or never put and personal data on it, you might be alright.  The other mistake was not including the 19GB of unallocated space in the Extended partition.  Poor setup.

I'd copy all the personal data to another hard drive and start over.

---

### Post by gordintoronto on 2016-04-04
In the short term, this command might help:
sudo apt-get clean

(This deletes the package files which have been downloaded to install program upgrades. Once the installation is done, there is no need to keep the .deb files.

---

