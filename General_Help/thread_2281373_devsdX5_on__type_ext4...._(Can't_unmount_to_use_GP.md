---
title: "/dev/sdX5 on / type ext4.... (Can't unmount to use GParted)"
date: 2015-06-06
forum: General Help
---

### Post by imzack2 on 2015-06-06
I am trying to use up the unallocated space on my SSD, but I cannot move some of my partitions since they are locked, and say they are mounted... (tried unmounting them)

Please take a look at the attachments, they might be able to explain my issue then I can in words...

I am trying to use Gparted to move the partitions around... but they appear locked.

[IMG]http://i61.tinypic.com/f253wg.jpg[/IMG]

[IMG]http://i62.tinypic.com/t71yyo.jpg[/IMG]

[IMG]http://i59.tinypic.com/2hrla9l.jpg[/IMG]

[IMG]http://i60.tinypic.com/15naxz9.jpg[/IMG]

[IMG]http://i58.tinypic.com/vore3a.jpg[/IMG]



Any Ideas/thoughts?

---

### Post by Bashing-om on 2015-06-06
imzack2; Hello;

What pops to mind, and you have not said. is the medium that you are working from to effect this moving of partitions.

Are you working from the liveDVD(USB) ? One can not unmount a filesystem that is in use ( hard drive) ; which is why the requirement for the liveDVD. - A bit more involved is to boot from the sda drive, manually make sure sdb is UNmounted, and then one can work on sdb from sda .


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-06-06
You seem to be trying to work on partitions of your installed OS which can not be done; you can not unmount partitions that are part of the OS in use.

However, I am totally confused about which partitions are which on your system as there appear to be two separate Linux OS root partitions, ie sda5 and sdb5, so it would be helpful to know which OS you are booted into and whether or not the other one is still used.  Whatever the answer to that, boot to a live system (DVD or USB) which has gparted installed by default and use that instead of the installed OS; it is always much safer to use a live system for these activities in my opinion, and mostly, it is the only way..

You will still need to use "swapoff" by right clicking in sdb6 as the live system will find and use that automatically, and you will then probably need to unmount the extended partition sdb3 but once all are unmounted and swap is not in use, you can do what you want.

The easiest and quickest way forward is to make a new partition of either ext4 if it is for ubuntu only, or ntfs if you want to use it for both OSs.  If you really want to add it to your ubuntu partition you will have to move or delete the swap partition (deleting is quicker) then extend the ubuntu partition into the unallocated space, leaving a 4GB space to add back a new swap at the end.

Extending the partition will take a very long time and it is imperative that you do not interrupt that in any way, so if this is a laptop, make sure it is plugged into a power supply first.  If you choose to make a new partition it will be a very quick job, and will then not need to move swap but can leave it where it is.

If the new partition is ext4 you can use it as your /home if you want to, or you can just leave it as a data partition (ext4 or ntfs - see earlier comment), but either way you will have to edit /etc/fstab to automount the new partition, either as /home or as a new data partition.

Come back for more details, depending on your choice.

---

### Post by Bucky Ball on 2015-06-06
As above: boot from the live media> Try Ubuntu> when at a desktop, launch Gparted> right click and unmount partition (should already be unmounted)> resize.

Just a note: Please attach large pics by using 'Go Advanced' or 'Adv Reply' and using the paperclip icon in the toolbar there rather than inserting big pics in the body of your posts. Thanks. ;)

---

### Post by imzack2 on 2015-06-06
I am not booted off the hard drive I am trying to modify...

I am booted off a HDD, and have the SSD connected to my laptop via a SATA to USB cable.

SDA is my HDD, SDB is the SSD that I am trying to re-partition.

Also, swap is turned off

---

### Post by Bashing-om on 2015-06-06
imzack2; Humm ...

Strange issue then ..
Booting from 'sda' one should be able to work on 'sdb' partitions IF there are no file systems mounted on 'sdb' .
So Is there ?
```

sudo swapoff -a
mount
cat /proc/mounts
cat /etc/mtab
df -h

```
Please post these outputs between code tags.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]let's see what tale is told
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-06-06
> **Bashing-om said:**
> 
Strange issue then ..
Booting from 'sda' one should be able to work on 'sdb' partitions IF there are no file systems mounted on 'sdb' .
So Is there ?


Exactly. When you are looking at sdb via Gparted on the sda boot, right click a the partition you are trying to resize. Unmounted? Might be a silly suggestion if that is what you're already doing, but doesn't hurt to confirm ...

---

