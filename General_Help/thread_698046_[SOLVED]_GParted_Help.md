---
title: "[SOLVED] GParted Help"
date: 2008-02-15
forum: General Help
---

### Post by zoso375 on 2008-02-15
I have unallocated space on my hard drive (/dev/sda4) that I want to completely wipe out and allocate said space to my ubuntu partition (/dev/sda3).  I'm moderately versed in Ubuntu, but very noob when it comes to GParted.  I can't, as of now, delete /sda4 because it's an extended partition.  Any way to get around that?  Also, I assume I would have to create a new linux swap partition (I've allocated a bit of space on /sda3 for that), but do I need to do something to make the ubuntu partition "point" to that?  Here is a screenshot: 

[IMG]http://img514.imageshack.us/img514/2337/screenshotdevsdagpartedik0.png[/IMG]

Can anyone tell me exactly how to go about this?  Thanks in advance.

---

### Post by Zeroangel on 2008-02-15
I would suggest

Right click on the linux-swap partition and select 'swapoff'. Then delete it. (you can't delete filesystems that are in use -- hence disabling it via swapoff) then deleting the swap partition.

You should now be able to remove the extended partition.

It would probably be a better idea to just keep the extended partition and change the swap file over to the unallocated space prior to the extended partition. And just put a filesystem inside of the extended.

FYI there is a limit to the number of filesystems you can have before you need to start creating extended partitions to put them inside of. I think that number is '4' -- which might explain your current problem.
-----------------
When you want to put the swap partition back, just open the 'fstab' file as root. One way of doing this is pressing ALT-F2 and using the command.
```
gksudo gedit /etc/fstab
```Make sure there is a line in there similar to this one
```
/dev/sda5 none swap sw 0 0
```Of course replace /dev/sda5 with the dev of your actual linux-swap filesystem

---

### Post by accatagon on 2008-02-15
I'm assuming they won't let you delete /dev/sda4 because it contains at least one logical partition first. Try deleting the logical partition and then deleting the extended one. If you end up deleting the partition, you will need to change fstab on Ubuntu to point to the new swap partition. Of course, you could just move the swap all the way to the right, shrink the extended partition, and then expand /dev/sda3. 

If you need help with fstab and swap, I've dealt with it before, so just leave another message if you decide to delete the last partition or if suddenly you lose your swap partition. 

But, to make a long story short. . . there should be a line like this in your fstab:
```

UUID=f421c402-1144-7189-26c0-4dbfb06a724c none            swap    sw              0       0

```

The UUID needs to match that of the swap partition, which can be found at /dev/disk/by-uuid by using "ls -al." You can also just use the name of the swap partition in place of the UUID if you wish.

---

### Post by zoso375 on 2008-02-15
Thanks for the help, guys.  I just moved the swap partition all the way to the right, shrunk the extended, and I'll boot with a live CD to expand sda3.  All I was really trying to do was put the space back on my ubuntu partition, so...simpler is better :)  And thanks for the above and beyond knowledge, for which I'm always thirsty.  I do understand a little more about partition editing.  As soon as I expand sda3, I'll mark this post solved.  Thanks again.

---

