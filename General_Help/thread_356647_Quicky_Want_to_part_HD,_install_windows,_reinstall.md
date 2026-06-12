---
title: "Quicky: Want to part HD, install windows, reinstall grub - safely"
date: 2007-02-08
forum: General Help
---

### Post by SimonTheMime on 2007-02-08
I have Linux on the full hard drive. I want to safely partition, install Windows on the other partition, then install grub.

How would I go about all of this.

Thanks in advance.

---

### Post by scrooge_74 on 2007-02-09
Use Gparted from a live CD, you cant repartition a mounted drive so using the live CD is the way to go.  When you install Windows and tell it where you want it to go, you are going to need to reinstall GRUB so it can boot your Linux box.  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by iammeagain on 2007-02-09
There are probably a ton of how to's if you google search but I don't really wanna do my HW at this moment so I'll type you a how to. This is my first so don't be to hard on me, but I have done this a few times. Oops looks like someone beat me too it, w/e ill just leave this here for reference.

[U][SIZE="5"]
Before anything else back up data, or at least the data you really care about. [/SIZE][/U]

[SIZE="2"]**Partitioning and Installing:**[/SIZE]

_First_ You would want to boot a live Ubuntu CD

_Second_ Once its loaded start gparted, *(I think it might be under the System menu then the Administration, but search elsewhere if you don't find it i know its somewhere. If you completely can't find it open a terminal and type in **" sudo gparted "**  (no quotes))*

_Third_ With gparted resize your Ubuntu partition, or do it however you want to make another partition for Windows. *(I don't believe you need to format it to anything, because you will format it anyways with the windows installer.)*

_Fourth_ Tell gparted to apply the changes and reboot.

_Fifth_ You now have to install windows, boot the Windows install CD and choose the right partition. Install it... wait a long time....

**[SIZE="2"]Install Grub:[/SIZE]**

*Info* Windows erased the Master Boot Record (MBR) so now we have to fix that.

_First_ Boot into Ubuntu live Cd again

_Second_ Open up a terminal, and type in [B]" sudo grub "
[/B]
_Third_ Type **" root (hd0,1) "** Replacing the 0,1 with the appropriate #'s.* (You need to know what partition Ubuntu is on. If you can't remember opening a new terminal and typing " sudo fdisk -l ", which will list your partitions. So hda1=hd0,0   and  hda2=hd0,1   and  hdb1=hd1,0  I hope that makes sense its a little tricky to explain.)*

_Fourth_ Type in **" setup (hd0) "*** (But replace it with the same thing it was above for you.)*
[U]
Fifth[/U] Type **" quit "** and reboot everything should be setup. *(Once you learn how its not nearly as hard as it seems.)*

---

