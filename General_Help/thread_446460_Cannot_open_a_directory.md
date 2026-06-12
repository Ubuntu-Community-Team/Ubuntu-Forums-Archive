---
title: "Cannot open a directory"
date: 2007-05-17
forum: General Help
---

### Post by valuntahr on 2007-05-17
For some strange reason the contents of a folder on my system fails to load. I was working perfectly when I was accessing it just a couple days ago, and I haven't changed any configuration files since then other than the usual Ubuntu updates. The folder is a mountpoint for a hard drive that I store some media files on to be accessed through the network. When I try and access it through Samba on my windows XP laptop I just get an empty folder listing. When I try accessing it through the Gnome GUI I get an error message saying that Ubuntu cannot open the folder. And when I try and open it through ls in the terminal I get a ls: reading directory /Music: Input/Output Error. I know that the data is still in the folder as the free space in the folder is at the value that it should be instead of increasing to the capacity of the Hard Drive. The really odd thing is that my other network share still works perfectly. I've tried the solution in the cannot access windows share thread but that solution didn't work, so I'm wondering if it might be something more fundamental than just a simple samba error. Thanks in advance.

---

### Post by joft on 2007-05-17
What is the filesystem of this particular partition?
Is the partition really mounted? Check with a call to "mount". Then you'll also see the device node (/dev/XXX), which is associated with this partition. Have look at the output of "dmesg" or the contents of /var/log/syslog before and after you try to access the mount point and watch out for warnings/errors regarding the device node.
You can also do this while trying to unmount and remount the partition. There might be errors while the kernel is trying to mount the partition.

---

### Post by valuntahr on 2007-05-17
the file system is ext3, and the drive is mounted correctly according to mount. However after doing some poking around in fstab and Gparted I noticed something odd. There are 2 hard drives that are not showing up as they should. One is the mountpoint I"m having trouble with, and the other is a spare drive that I don't use very often. Is there anything software related that could cause both hard drives to spontaneously not show up like this? or should I start worrying about a hardware related issue at this point? Right now I'm leaning towards it potentially being a hardware issue, but I'd like to have that confirmed if at all possible before worrying about potentially replacing the hard drives..

---

### Post by valuntahr on 2007-05-19
any ideas on how I can resolve this short of swapping hard drives?

---

### Post by joft on 2007-05-20
Sorry for this late answer. Hmmm, did you look at the output of ```
dmesg
``` ? Or the contents of your system log file /var/log/syslog, as I asked before?
Or, did you try to umount/re-mount ```
umount /dev/XXX
dmesg
mount /dev/XXX
dmesg
```
Then, are there any new lines in dmesg's output after calling it the second time?

I think we need a bit more info here. Could you please post the output of
```

sudo cat /proc/partitions

sudo mount

sudo cat /etc/fstab

sudo fdisk -l

```

and perhaps a part of dmesg's output. Or, just post the whole output, if your are in doubt what to post. If it is an ext3, there should be error messages regarding the partition/hard drive in question.
Or, if the is hardware problem, unable to read sectors e.g., there should be some error messages, too.

---

