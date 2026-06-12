---
title: "Help with grub command for windows boot."
date: 2008-06-26
forum: General Help
---

### Post by azrale on 2008-06-26
I recently reloaded my pc. I accidentally installed my windows on the second partition. I need to know what to type in the grub command to get my windows install to boot. I can boot fine into ubuntu but i cannot find the right command to edit My GRUB. Here is some info. 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5384aadb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19456   156280288+   f  W95 Ext'd (LBA)
/dev/sda5            2551       19456   135797413+   7  HPFS/NTFS
/dev/sda6               1        2468    19824115+  83  Linux
/dev/sda7            2469        2550      658633+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@Dreys:/home/mduff# cat /boot/grub/device.map
(hd0)	/dev/sda
root@Dreys:/home/mduff# gksudo gedit /boot/grub/menu.lst

---

### Post by azrale on 2008-06-26
Basically i cannot figure out what to use for the windows partition. i found this but i am note sure what to type in between the parentheses. thanks in advance for the help. 

title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by WRDN on 2008-06-26
To edit the GRUB menu.lst file, type in the terminal:

```
sudo gedit /boot/grub/menu.lst
```

Now, if it doesn't already exist, you may want to add this divider at the bottom of the menu.lst file:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```

The following has been copied from my menu.lst file:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

Based on the information you provided, that Windows is on '/dev/sda5', you would need to change the "root (hd0,X)" line (X being a number) to 'root (hd0,4)', as seen above.

So, in summary, add the following lines to the bottom of the menu.lst file:

[B]```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```[/B]

---

### Post by jualin on 2008-06-26
I think that the change is from "hd0,0" to "hd0,4". Maybe someone else can confirm this.

---

### Post by azrale on 2008-06-26
When using (hd0,4) i am getting "error 12: invalid device requested."

---

### Post by jualin on 2008-06-26
--------------------------------

---

### Post by WRDN on 2008-06-26
julian, the "#" at the start of the line is used to show it is a comment. It is purely for people to read, and the computer ignores it.

azrale, please could you post the entire contents of the menu.lst file here.

---

### Post by jualin on 2008-06-26
That's true I forgot about that

---

### Post by jualin on 2008-06-26
This user explain very good how to set up Grub [http://ubuntuforums.org/showpost.php?p=5267216&postcount=4]("http://ubuntuforums.org/showpost.php?p=5267216&postcount=4")

*edit* According to your results I think that maybe changing(hd0,0) to (hd0,1) will work for you. but I don't know if since your Windows partition is on the second line it is considere (hd0,1) or (hd4,0) since is on the sda5 partition.

---

### Post by bodhi.zazen on 2008-06-26
First of all, can you confirm where you installed windows ? Which partition ?
 You stated "I accidentally installed my windows on the second partition." which partition is that ? we are guessing sda5.

Second, if windows is on sda5 , well that will not work. Windows needs to be installed into a primary partition and sda5 is a logical partition.

**I think this is your problem, you have no primary partition and windows needs to be installed into a primary partition.**

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Third, to boot windows if it on the second (slave) hard drive you need to map the hard drives.

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

Fourth, if you have more then 1 windows installation you need to hide them from each other.

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

:lolflag:

---

