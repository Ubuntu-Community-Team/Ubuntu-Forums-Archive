---
title: "/media folder - number added to external drive"
date: 2017-08-22
forum: General Help
---

### Post by mQzFFMP on 2017-08-22
Dear all,

I need your help with a strange behaviour I am experiencing in Ubuntu.

I use a external USB disk drive with 4 partitions named A, B, C and D. I use these partitions for various purposes across my system, such as backing up, syncing etc. The related applications rely on the partitions' names.

I have observed that some of those applications do not "find" the partitions any more, although I can view their contents.

I think I have found the cause. If I go to the /media/my_name folder, I see that there are "placeholders" for the partitions A, B, C and D, but also for A1, B1, C1 and D1, which are now the ones actually pointing to the USB drive. If I disconnect the drive, A1, B1, C1 and D1 disappear, but A, B, C and D do not, and I do not know how to delete them. The commands cd and rd indicate "No such file or directory".

Can you please let me know how can I ensure that my drive is again assigned the right partition names?

Thanks a lot!

---

### Post by Dennis N on 2017-08-22
When you hot plug in a USB drive, it automounts any file systems (partitions) on it at mount points under /media/<username>/ based on the root folder of the file system. When you eject the drive, those folder names are normally deleted. But, if the drive is not properly ejected, then the mount point folders created can remain behind. In that case, next time you plug it in, the system follows the rules for mounting USB, which is to create folders. Since the folder names A,B, ... already exist, it creates new ones by adding a number.

**rd** is not a linux command. Since the folders are empty, you can use **rmdir** to remove them with the drive unplugged.

---

### Post by Morbius1 on 2017-08-22
Another possible cause is that you defined A, B, C, and D in fstab under /media/$USER but pointing to another device(s). Take a look at /etc/fstab:
```
cat /etc/fstab
```

---

### Post by ajgreeny on 2017-08-22
If you want those 4 partitions to always mount in the same place, ie **/media/<username>/A**, (or B, C or D), even when hot plugged, the easiest way is to give a label to each partition using, for example, gparted.

When hot plugged they will always now mount to /media/<username>/A, etc etc,

As Dennis N says, you **must always unmount** or eject those partitions before unplugging them, just as you should always do in Windows, or corruption of their contents is a possibility; I hope you always do so, but if you don't, please start to do so from now on.

---

### Post by mQzFFMP on 2017-08-23
Thanks a lot, I managed to delete the leftover mount point folders with **sudo rmdir **etc., and when I replugged the drive, the partitions recovered their proper names.
Thanks for helping out!

---

