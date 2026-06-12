---
title: "GParted libparted problem workaround  &quot;should reboot now before further changes&quot;"
date: 2016-07-06
forum: General Help
---

### Post by NuxNik on 2016-07-06
Having searched for previous issues with 
[COLOR=#000000]Partition(s) 1, 3 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use. [/COLOR][COLOR=#000000]You should reboot now before making further changes[/COLOR][COLOR=#000000]

[/COLOR]http://ubuntuforums.org/showthread.php?t=1236873&page=3

And not wanting to reboot to solve the issue, I have found a workaround using the gnome-disks utility that avoids a reboot
[COLOR=#000000]
[/COLOR]All you need to do is access the appropriate device in disks, remove the partitions, format a small a small partition and mount it.
(all within disks)


Then refreshing your devices in gparted, will give you access to the device and it's new partition
Using gparted, remove all and continue with what you were doing


I'm also assuming that backup images were made before trying to manipulate the device with gparted.


This is a problem that was reported back in 2009 
[http://ubuntuforums.org/showthread.php?t=1236873&page=3](http://ubuntuforums.org/showthread.php?t=1236873&page=3)
and clearly NOT resolved.
[COLOR=#000000]

[/COLOR]

---

