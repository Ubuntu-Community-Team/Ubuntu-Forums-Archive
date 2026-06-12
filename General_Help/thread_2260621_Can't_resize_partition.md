---
title: "Can't resize partition"
date: 2015-01-13
forum: General Help
---

### Post by Hvidemose on 2015-01-13
[LEFT]I would like to resize my Ubuntu 14.04 partition (sda8), so it has more gb. I have this unallocated space. I'm doal booting with Win 8, and there are several small partitions, that is used by the win system (for recovery or what ever we call it).
[/LEFT]
 [LEFT]The problem is, that I cant merge the sda8 and the unallocated, even though booth are ext4 format. I have tried GParted and kvpm both in Ubuntu and from usb. It just cant be done. Even if they are not mounted....
I have added a screenshot from GParted.
[/LEFT]
 [LEFT]Is there a way that this can be done?

[ATTACH=CONFIG]259216[/ATTACH]
[/LEFT]

---

### Post by stalkingwolf on 2015-01-13
you may need to do a fresh install. make the unallocated part into a logicical partition? then install. you can only have 4 primary partitions. I recently ran into this.  OEM manufacturers lock the hard drive up by having 2 partitions for the system 1 for system rescue and a 4th for their "tools".  to create a partition you have to remove one of the exisitng ones.  I removed the hptools partition (with the owners permission) created the necessary space and got on with what i needed to do.

---

### Post by oldfred on 2015-01-13
You have sda5 in between, you have to backup & delete sda5 to be able to rearrange.
And with any partition changes, you need to have good backups of all your Windows system and data.

But my normal suggestion is smaller system partitions for both Windows & Ubuntu and large data partitions. Windows needs a much large system partition than Ubuntu, but for Ubuntu I create a 25GB / (root) partition and only use about 11GB. But have all data in either a NTFS data partition for any data I might share with Windows or in a Linux data partition. And alternative for newer uses is a separate /home which has all data and the user settings.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Hvidemose on 2015-01-13
Cheers for the fast replies!

Ok, but do I need any of the partitions besides the recovery (sda2)?

---

### Post by oldfred on 2015-01-13
Windows requires several as does Ubuntu, not sure you can delete any.
Once you have made the vendor backup set of DVDs, that partition has less value. And when drive fails you need the DVD set anyway.

---

