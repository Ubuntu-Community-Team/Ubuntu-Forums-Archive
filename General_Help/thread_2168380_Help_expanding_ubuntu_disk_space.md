---
title: "Help expanding ubuntu disk space"
date: 2013-08-17
forum: General Help
---

### Post by Roopam_Poddar on 2013-08-17
Hi,
Currently I have a dual boot system ( windows 7 and ubuntu ). The later is showing low disk space. Following some links on the internet I have shrunk one of the volumes of windows 7 and thus have some un allocated space. But I am not able to expand my current ubuntu partition onto the unallocated space. 
Also strangely gParted is not showing any ext3 partiton. All are ntfs.
I fear something is bad.

Please suggest.
Attaching screenshot.

[IMG]http://i.imgur.com/NSUoC5a.png[/IMG]

---

### Post by newb85 on 2013-08-17
The lack of an Ext* system is really disconcerting.  Are you running Gparted from a Live disc, or from your Ubuntu install?

Also, typically Windows is listed first in a dual-boot situation.  Shrinking the first partition shouldn't have resulted in empty space at the *end* of the drive...

---

### Post by Mark Phelps on 2013-08-17
You do NOT have an Ubuntu "partition" -- if you did, you would see it in the Disk Management results.

You installed using Wubi, which creates a single file "root.disk" which serves as the Linux filesystem.  The limit on the size of that file is 30GB.  I'm not aware that you can make it any larger.  You wouldn't see this in Disk Management because it is a single file, not a partition.

There is literally no way to expand Ubuntu to use the unallocated space and keep the Wubi install.

Sorry, but you would have to uninstall Ubuntu and then re-install it, this time, from the bootable media, and to the unallocated space.

---

### Post by ajgreeny on 2013-08-17
It is possible to migrate a wubi installation to a full partitioned install. [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

I have never used wubi and have no real idea how easy or successful this migration is, so will have to leave you to search more on that subject.

---

### Post by chkneater on 2013-08-17
simply login to sda2 (linux install) use gparted to unmount and move sda3 to the unallocated space (I assume is the windows partitiion) and use the slider to expand sda2 ( the UBuntu install, not Wubi, correct? ubuntu can be installed under ntfs, and since you said nothing about wubi I have no reason to think you are using it)  Either way, you can expand sda2 since you are expanding the disk space available and not the OS itself so say for instance you DID install Wubi, the disk space would be availble to you regardless.  I must mention, SOMETIMES (hasn't happened for a while) info can get messed up when moving, but I doubt it will in your case, just so you know.

Also might I suggest an NTFS partition that you share between Windows and Ubuntu, that way if you make changes to either OS that destroys it, the NTFS filesystem (just empty space, no OS, make folders in it tho) will still have your docs, music, movies and all that junk.  I do this as a backup cuz I like to eff around with different OS's.

Oh, and there is nothing wrong with your system, no fear.

---

### Post by Roopam_Poddar on 2013-08-18
Yes, it is indeed Wubi. I found the root.disk file in the D drive of  windows. So I guess the only real solution is to reinstall ubuntu in a  new partition. 
But before that I'll try to move the wubi installtion to a new partition as described in the wiki : [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) and will post here if this was successful.
Thanks guys for the support and comments.

---

### Post by QIII on 2013-08-18
Hello!

Please, please, please!  [U][I]Back up any important data you have on BOTH Windows and Ubuntu before you do anything!
[/I][/U]
Recovering data when something goes horribly wrong can be difficult or impossible if you make major changes.

---

### Post by chkneater on 2013-08-18
You stated that you had ubuntu (or wubi, whatever) and win7 and that you downsized your win7 partition, leaving unallaocated space, correct?  Which partitions are they on?  To my eyes it looks like you had windows on sda3 and have Linux on sda2.  What problems have you encountered in simply moving sda3 OVER to the unallocated space (while booted in sda2 or Live CD with gparted on it) with the little slider in gparted and then resizing sda2?  To me that is the more simpler answer than reinstalling... and what do you mean be 'reinstalling ubuntu in another partition'?  If wubi is sda2, just leave it there?! and move sda3 over, just sayin...  And are you trying to have 3 OS's on here because you say ubuntu installation and wubi and windows.  Clarify a little here

---

### Post by Roopam_Poddar on 2013-08-18
No, I am just trying to have two OSs : Ubuntu and Win7. 

I downsized my sda3 leaving unallocated space as you can see in the screenshot, hoping to assign that space to the ubuntu partition ( which I thought existed untill Mark Phelps suggested I have Wubi instead, which I couldn't recall at the moment). 
Confirmation for the same was provided by the following points:
    1. Non-existence of any ext3 partition.
    2. Existence of root.disk wubi file in sda3 ( which is the D drive in win7 on my system) (screenshot attached)
Thus I have windows in sda2  ( C: drive ) and Wubi installed on sda3 ( D: drive )

I am planning to create a new partition from the unallocated space and then shifting the wubi installtion of ubuntu to that new partition and thus hoping to solve my low disk space problem as a Wubi installtion of ubuntu has limited disk space available (30G).

[IMG]http://i.imgur.com/WYSXrG6.jpg[/IMG]

---

### Post by Roopam_Poddar on 2013-08-18
Thanks for the heads up man! I sure will :)

---

### Post by ajgreeny on 2013-08-18
> **chkneater said:**
> You stated that you had ubuntu (or wubi, whatever) and win7 and that you downsized your win7 partition, leaving unallaocated space, correct?  Which partitions are they on?  To my eyes it looks like you had windows on sda3 and have Linux on sda2.  What problems have you encountered in simply moving sda3 OVER to the unallocated space (while booted in sda2 or Live CD with gparted on it) with the little slider in gparted and then resizing sda2?  To me that is the more simpler answer than reinstalling... and what do you mean be 'reinstalling ubuntu in another partition'?  If wubi is sda2, just leave it there?! and move sda3 over, just sayin...  And are you trying to have 3 OS's on here because you say ubuntu installation and wubi and windows.  Clarify a little here

Sorry chkneater but you have completely misunderstood what wubi is, and the partition information given so far.
There is NO LINUX PARTITION on sda2; it is a ntfs partition so is windows, not linux.

When ubuntu is installed as a wubi installation it is simply another application in windows and can be uninstalled in the same way as any other windows application.

---

### Post by chkneater on 2013-08-19
Regardless of how wubi works, the process for changing its size is different?  And I did actually understand the partitioning perfectly clearly if you have read the later posts: sda2 is WUbi and sda3 is Windows.  The unallocated space sits behind Windows because that was the partition downsized.  If I am wrong, explain then how to fix the problem...

---

### Post by newb85 on 2013-08-19
Wubi doesn't install to a normal partition.  It installs to a virtual partition.  sda2 and sda3 are both Windows partitions (which I'm guessing both existed before you did your Wubi install).  Your Wubi install is on one of those, but it is likely not the only thing on that partition.

---

### Post by ajgreeny on 2013-08-19
> **newb85 said:**
> Wubi doesn't install to a normal partition.  It installs to a virtual partition.  sda2 and sda3 are both Windows partitions (which I'm guessing both existed before you did your Wubi install).  Your Wubi install is on one of those, but it is likely not the only thing on that partition.

@ chkneater.

I do not need to say any more.

---

### Post by emiliano2 on 2013-08-25
Just wanted to say that I'm also in the same boat as you Roopam_Podder and I hope you posts how it all went because I'm interested to know of any difficulties you may have had.  I'm looking to flip my install from using wubi to a dedicated partition too, but I'm hesitant because frankly I'm a noob to it....

---

