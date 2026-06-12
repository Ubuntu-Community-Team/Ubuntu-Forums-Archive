---
title: "Moving dualboot to SSD - how to?"
date: 2012-11-27
forum: General Help
---

### Post by Aeefire on 2012-11-27
Hey guys, I am here to ask a question, which might have been asked several times already - and i am sorry for that, but i have read through websites for hours but can't find a description which allows me to do the job without too high risk (e.g. choosing something which i don't know what it actually does)

So what I what I have: ubuntu 12.10 lts and windows 7 64bit

I do have 5 partitions:
root ubuntu w/ 93,13 gb
/swap ubuntu w/ 11,18 gb
/home ubuntu w/ 18,63 gb

C:/ Windows, NTFS  804,48gb
:/ SYSTEM (Windows) "active", NTFS 100 mb

So what I want to do is: move :/ SYSTEM , C:/ , root, swap and home to my new Samsung SSD 830 with 256 gb (certainly, i would shrink all partitions down to fit on it, with some space left, anything to be aware of, when doing this?


So currently, I am pretty clueless on how to do this.
I have already used gparted for some minor stuff and now downloaded clonezilla (and burned to a cd).

which tool is preferable? (some on the forums say gparted, because dualboot isn't handled correctly by clonezilla etc.. or a combination of both?)
Can i do the partition-shrinking on my "old" ubuntu installation or better with a live cd?
which partitions do i have to move first? (and how?)
in which sequence do these partitions have to be moved? (or doesn't it matter?)
is there anything to do before first boot, after movement is completed? (i read something about "allignment" and stuff...)
is there anything else to be aware of?


Thanks for everything!

---

### Post by LiamOS on 2012-11-27
Moving linux to a new disk or partition scheme is trivial. All you have to do is copy everything to where it should be an edit /etc/fstab accordingly.

Moving Windows to a new partition scheme is, in my experience, a horrifying experience. It may be possible, but I wouldn't expect it to be so.

I'd seriously consider a reinstall of windows, and copying over your ubuntu installation if you're comfortable with manual partitioning and tar use.

---

### Post by apochry on 2012-11-27
You can copy all partitions to the ssd using [GParted]("https://apps.ubuntu.com/cat/applications/precise/gparted/") and than run [Bootrepair]("https://help.ubuntu.com/community/Boot-Repair").
It worked fairly well with the Linux partition for me several months ago. I doubt it will succeed with Windows, haven't tried it thought.

Regards,
Christo

---

### Post by Aeefire on 2012-11-27
Yes, reinstalling windows is (still) an option. I mean.. if not now, when then?
However, I'd like to consider using Windows 8 for this then (I am a student and i get free licenses for it).

But ok, I guess a fresh installation of windows 7/8 makes less problems.

Ye... manual partitioning and tar usage.. 
So how would the process look like?
1. disconnect (old) primary drive
2. connect SSD
3. install win7 or 8 on it.
4. reconnect old hdd
5. boot a gparted cd
6. shrink windows C:/ partiton to some reasonable amount
7. "move the [old] ubuntu partitions" to the ssd (i believe there is some function inside gparted for this)
8. reboot (and pull out cd)

So you said "just copy the data over".. and edit some config-file right? 
Is this step "skippable" if gparted has such a "move partition function" ?

Is there nothing to be aware of because of using a SSD (as i said in the opening post.. "allignment" and stuff).. or does windows manage this? (i've heard something like that somewhere)

---

### Post by oldfred on 2012-11-28
How new is computer? Is is BIOS/MBR or UEFI/gpt?

Even with Ubuntu I would do a new install. You can copy but have to change UUIDs if re-using old drive with same UUID. And then you have to reinstall grub2 to update it to new UUID and edit fstab with new UUID. There are one or two other updates that should  be done. Grub remembers which drive to reinstall to so it is a full reinstall of grub not just an update.
I have tried to help a couple of users who copied, but unless comfortable editing and update from liveCD it is not trivial.
Most of your user configuration is in your /home so that is what you want to copy. I separate /home user settings (the hidden . files) and leave those in /home on my SSD, but have all my data (the not hidden folders) on my rotating drives. 

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

I would also leave old Ubuntu install on rotating drive but shrink to very small like 10GB. I like to have a bootable system on every drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive. I used to rotate from drive to drive. Now with my SSD, I have two / (root) partitions on SSD and then test installs or one that also boots on every other rotating drive.

---

### Post by dcstar on 2012-11-28
> **Aeefire said:**
> 
........
is there anything to do before first boot, after movement is completed? (i read something about "alignment" and stuff...)
is there anything else to be aware of?


Existing /etc/fstab EXT4 entries will need the "discard" option added.

Accessing non-TRIM supported filesystems on the SSD via Linux will result in eventual performance loss as writes will consume vacant SSD resources but never free up the old blocks.

---

### Post by Aeefire on 2012-11-28
so let's say i reinstall both win7/8 and ubuntu on the ssd, and copy over the ubuntu /home stuff.
Can I leave the old "bootable" OS on the (now) secondary HDD when I set the SSD as primary HDD in BIOS?

What would the best partition-sizing for a 256gb SSD for ubuntu?

---

### Post by oldfred on 2012-11-28
I have a 64GB SSD with two / partitions. Currently my main Precise & Quantal for testing. 
I used 28GB for / and that includes my /home but no data. I have used about 9GB of the 28GB and about 2GB is /home but that is mostly .wine as that is the only data folder I have not moved to my rotating drive.
I have 4GB of RAM and rarely use swap, so just to have some swap I have it on rotating drive.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

    
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

On my 640GB data drive sdc I have many other Ubuntu installs for testing or my older installs from before my SSD. Almost all my / (root) installs are 25GB and all data is in other partitions which I have used with every install for the last 3 years.

---

### Post by Aeefire on 2012-11-28
SO currently i am trying to install win7. 

I made a bootable win7 usb stick (with the windows tool) .. win7 boots fine from the stick, but after the "loading files" screen, at a nice blue background the whole thing doesn't go on. I can move my cursor and stuff, but nothing proceeds..

---

