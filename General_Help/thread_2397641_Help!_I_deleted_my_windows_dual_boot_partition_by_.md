---
title: "Help! I deleted my windows dual boot partition by accident in ubuntu"
date: 2018-08-01
forum: General Help
---

### Post by liam-newell on 2018-08-01
In an attempt to delete my swap(bad idea) I ended up deleting my windows dual boot partition. I tried using testdisk but it keeps returning ```
No harddisk found

```

,however, when i run gparted and try data recovery I can mount the erased partition. I can also see it with fdisk but im not sure what all the loop partitions are about 

```

Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9A32532C-DF59-46FD-B5B1-D7A56DB26BFD


Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2   1050624 331180031 330129408 157.4G Linux filesystem
/dev/nvme0n1p3 331180032 331212799     32768    16M Microsoft reserved
/dev/nvme0n1p5 475373568 500117503  24743936  11.8G Linux swap



``` I've left out all the loop partitions

Any help would be greatly appreciated, I just want to recover my windows to play video games again

---

### Post by oldfred on 2018-08-01
Each snap adds a loop partition.
 [https://snapcraft.io/](https://snapcraft.io/) 

      
 [https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

I think snaps may be a good thing for users with an older version of Ubuntu but want to run a newer software app as it includes all the reequired dependencies. Same if newer system, but want to run some older application that needs the old dependencies. 
But do not see snaps use for running current apps in current system. It duplicates dependencies.

---

### Post by liam-newell on 2018-08-01
My bad I'll remove those I think it will confuse people of my topic

---

### Post by oldfred on 2018-08-01
You may be able to use testdisk or parted rescue to restore /dev/nvme0n1p4.

       Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/nvme0n1 > PT_nvme0n1.txt
So you know sectors (you have this above):
sudo parted /dev/nvme0n1 unit s print 

Similar to this, but this was restoring a Linux partition that Windows deleted:
      
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)

---

### Post by liam-newell on 2018-08-02
I ended up using testdisk but i accidentally messed up the partition table because i selected intel over gpt.
After fixing that and applying the correct partitions (ubuntu now booted). I could see from Ubuntu that the full windows partition was available and present, unfortunately after booting to windows through grub it needed start up repair(which didn't work). I ended up reinstalling windows as a whole and repairing grub. rip rocketleague had to reinstall

---

### Post by oldfred on 2018-08-02
Grub only boots working Windows.
Or if Windows needs chkdsk, or if it turns fast startup/hibernation back on, then grub will not boot it.
If UEFI, you can directly boot Windows from UEFI menu. But if BIOS you have to temporarily reinstall Windows boot loader.
Or always have Windows repair disk or installer with repair console and Ubuntu live installer  of current versions of operating systems to be able to make repairs.

---

