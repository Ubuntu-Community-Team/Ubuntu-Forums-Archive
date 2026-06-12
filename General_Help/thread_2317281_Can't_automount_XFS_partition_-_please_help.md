---
title: "Can't automount XFS partition - please help?"
date: 2016-03-15
forum: General Help
---

### Post by Jan_Johansson on 2016-03-15
This is my friends netbook which is an Asus 1015h with 2GB Ram and 250GB HDD. 

Here is the problem when I go to "disks" under Preferences and choose /sda2 and settings then I can set the slider to ON and set the options to automount at startup and show in user interface - but when rebooting I get an error and can only chose S for skip or M for manually. I also get an error from within "Disks" if I try to mount the drive there(not at the laptop so can't post it here).

History: The system had OpenSuse Tumbleweed 32bit before, but it had too many errors and simply not user friendly - so we installed Lubuntu 14.04.4 LTS 32bit instead from Bootable USB with LiveCD - Started up in "Try Lubuntu without installing" and then ran the "Install it" from the desktop. Here we chose the "other options" and formatted the first partition to ext4 and set the mount point to / the second partition(/sda2) was not touched(the second partition is the XFS and made by OpenSuse). Everything went fine and I have no problem mounting the second partition in PCmanFM - I just can't set it to Automount.

Trying to figure out what is wrong I found that Gparted were not installed by default so I installed it. Gparted told me when looking at the second partitions information that it could not read it because xfsprogs and xfsdump were not installed - so I installed these from synaptics. That removed the ! from the second partition in Gparted, but did not change that I can't automount it. I then searched the net and it seems a whole lot of people have this problem - I tried some of the suggestions with no luck - even re-installed xfsprogs through sudo apt-get install xfsprogs from lxterminal(my preferred terminal). No luck, so here I am to get some help.

It's quite annoying since my friend has all his files and music on the second  partition(XFS) and everytime he wants to play music or read/write documents  - he has to open PCmanFM and mount the second partition first in order to  read the contents in other programs.

The Partition table is like this:

First partition: 43GB ext4 has Lubuntu and / and is named /sda
Second partition : 202GB XFS and is named /sda2
Third partition is Extended and has the swap partition inside


I read somewhere that its not possible(right now, maybe in the future) to resize XFS partitions and any attempts on this might break the system - please debunk this if its not true. 

Since the XFS partition contains all my friends data(188GB), we really don't want to loose that, we are located in the Philippines in the province and it's not that easy to get another drive to backup on. 

Is there a way fix this without loosing the data?

Hope someone can help with this:)

JBJ

EDIT: Wow, 6 days and no reply - are all the tech guys from ubuntu on vacation?

---

### Post by LewisTM on 2016-03-25
Hi there,
To automount a partition at boot time, the easiest way is to add an entry in your /etc/fstab file and have an empty directory ready for mounting it
Instructions can be found [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") 
I've never used the Disks tool to setup autmounts so I'm not sure what it does to your system config files. Could you please post the contents of your /etc/fstab file?
Thanks!

---

