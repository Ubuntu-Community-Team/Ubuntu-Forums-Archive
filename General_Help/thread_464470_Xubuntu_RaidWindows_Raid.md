---
title: "Xubuntu Raid/Windows Raid"
date: 2007-06-04
forum: General Help
---

### Post by SBFC on 2007-06-04
Hi all, have a question about dual booting, but it's a little more complicated than a normal dual boot (at least I think so).

I have two 500G SATA's that are currently running a mirrored raid with Xubuntu, and I plan to pick up a couple 160G SATA drive's tomorrow to use for Windows (been missing too many games). Right now my /boot partition is installed on the raid (since it's mirrored) and obviously the windows boot loader will be installed on one of the 160G drives. 

How in the world will I be able to boot into Xubuntu? Will I be forced to install my /boot partition to one of the 160G drives, which would render my mirrored raid unbootable if one of the 160G drives fails? 

Right now I have windows setup on a 20G IDE drive, and I find that I can't boot into Xubuntu...I've really no idea how to resolve this with /boot being directly on the mirrored raid. If need be I'll bite the bullet and install /boot to one of the 160G....but I was hoping there'd be another way.

Any help would be appreciated.

---

### Post by snobel on 2007-06-06
I don't have raid1 on my desktop machine, but otherwise I think it is a similar setup to what you want: The first drive has feisty on it, the second drive has more experimental installs, like windows and gutsy ;)

I assume your current disks are sda and sdb, which grub will see as hd0 and hd1. 
Before installing windows, remove the array and install one of the new disks as the first sata device. (This would probably be the 'sata-1' connector...)

When you have a basic xp install running, replace the array the way it was, and place the windows disk on the next sata connector (sata-3?). That should make grub see it as hd2. Boot xubuntu and add this to /boot/grub/menu.lst:

```

title           Windows XP
rootnoverify    (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
makeactive
chainloader     +1
```

(Remember to place it outside the auto-updated part...)
The 'map' commands make windows think it is on the first disk in the system, like when you installed it.

Reboot and see if you can boot to windows. If it works, set up raid-1 for windows. XP software raid is a better bet here than onboard 'fake raid', which might interfere with the map commands above. So if you have a controller that can be switched from raid mode to simple mode in the bios, do so before you start...

When raid is working on both OS'es, proceed to install your games and stuff.

---

### Post by SBFC on 2007-06-06
Thanks for the reply. However, I was under the impression that GRUB was not an option with /boot being installed on the RAID.

I'm having issues with booting into Xubuntu. I installed Windows first, and after Xubuntu is installed it just boots up into Windows. This is what lead me to believe I may have to install /boot to the XP disk.

EDIT:

Forgot to mention, if I unplug the XP disk Xubuntu will start up, so I know the installation was successful.

---

### Post by SBFC on 2007-06-06
Alright, I'm not even going to pretend I know what's going on...but now it works fine.

As I said above, I had disconnected the XP drive to test the Xubuntu installation. After I plugged the XP disk back in, my system started into Xubuntu. Restarted again holding Ctrl, and the LILO menu came up, chose Windows...and there it was.

I had unplugged nothing from my mobo. When I disconnected my drive, I just unplugged the cord from the drive itself. I'm clueless...but not unhappy. :P

---

