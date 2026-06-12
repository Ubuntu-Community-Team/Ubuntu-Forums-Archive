---
title: "how to resize ubuntu partitions after installation?"
date: 2015-04-09
forum: General Help
---

### Post by elim-qiu on 2015-04-09
I have a triple boot laptop with ubuntu 14.04 partitions / and /home.  I'd like to resize the partitions and make /home yields some space to /. how can I do it without stopping any OS from working?

Thanks

---

### Post by sudodus on 2015-04-09
0. Boot from another drive, for example your Ubuntu DVD/USB drive, which also contains ***gparted***.

1. Do not move the head end of the partition containing /boot (moving it will make booting fail). It is the root partition / (unless you have a separate /boot partition). If the /home partition is right after the root partition, you can shrink one of them and after that expand the other one into the unallocated space created.

The following link illustrates how to do something similar with gparted: [GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf")

---

### Post by elim-qiu on 2015-04-09
I did that trick with no success. Grub was installed in partition /. and /home is the next partition. I used the usb installer usb's GParted to shrink /home (push the starting point to the right), applied the action but got error. 

Looks like Gparted cannot do the job for me.

---

### Post by sudodus on 2015-04-09
That was bad luck!

- Please describe what error you got!
. Did you unmount the partitions before starting to edit them?
. Did you try to shrink it more than what is reasonable? There should be some margin för new programs plus at least 10% workspace (free space) in the root partition.

- Is your system working now, does it boot?

In that case, if you have not done it already, it may be a good idea to ***backup*** all important files (documents, pictures etc) before you continue.

It makes it easier to help, if you describe the partitions in your disk with the following command

```
sudo parted -l
```

You can do it when booted from USB.

---

### Post by elim-qiu on 2015-04-10
Thanks a lot sudodus! I didn't unmount the partitions that I'd like to resize. I guess that's the problem. The system is still working. I'll colonezilla the whole disk and try it again.

---

### Post by elim-qiu on 2015-05-07
Alright, GParted app from my ubuntu installer ssd did everything great for me!


My HDD partition
```

1)  XP                (NTFS)
2)  OSX_SYS    (HFS)
3)  extend partition
        OSX_USR     (HFS)
        Workplace     (NTFS)
        /          (Ubuntu sys, grub installed here  ext4)
        /home     (Ubuntu user home,           ext4)
4)  swap

```

partition 2) is active where osx boot menu will give you chance to boot from somewhere else.
grub was installed on  / (ubuntu sys)


My first try was not success, I thought it actually due to the partitions were almost full...

I used bleachbit cleaned up some disk space, than GParted helped me shrink swap partition (which never seem need more than 1G), and then make /home bigger.

The next try also very successful, I made / (ubuntu sys) shrink (where grub was installed) and then make /home even bigger.

I think /home should be big since the data here is very personal. The system can be change, but it just too costly every time   update os will lost user data...

---

### Post by sudodus on 2015-05-08
Congratulations :KS

If you are happy with this solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

