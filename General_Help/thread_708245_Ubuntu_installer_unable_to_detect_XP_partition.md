---
title: "Ubuntu installer unable to detect XP partition"
date: 2008-02-26
forum: General Help
---

### Post by linux2352 on 2008-02-26
My partition table of 160GB Hard disk are follows

Primary partition - 36GB NTFS            - Contains the windows XP

Extended partition 
            Logical Partition 1 : 55GB NTFS       -  contains some files         
            Logical Partition 2 : 30GB ext3        -  free
            Logical Partition 3 : 3GB Linux swap      
            Logical Partition 4 : 20GB ext3         - free
            Logical Partition 5 : 3GB Linux swap

I am kinda newbie to linux. I booted from my Ubuntu 7.10 livedvd and tried to install ubuntu in the 30GB partition. In the next step ubuntu installer was not able to detect any operating system installed on the computer . Previously when i tried to install ubuntu on another system it did actually detect an windows partition and imported the user documents from the XP partition . 

If I install ignoring the installer not detecting the XP partition then it will overwrite the master boot record to directly boot to ubuntu instead of showing a menu asking what partition to boot. This is my main problem

---

### Post by kellemes on 2008-02-26
The importing of documents etc.. isn't important, not for me at least..
If you instruct the installer to install Ubuntu on the partitions you created for it (ergo.. leave NTFS-partitions alone) XP won't be touched.

The bootloader shouldn't be any problem.. most often Ubuntu will put Windows in the bootlist, but if it doesn't you can easily add it to the list.
In /boot/grub/menu.lst you can add an entry for it (post back in case you need to).


By the way, always expect trouble.. ;-)
So backup your stuff.

Edit: By the way, why do you have 2 swap-paritions?
In case you want 2+ distro's installed.. you can have them share 1 swap-partition.

---

