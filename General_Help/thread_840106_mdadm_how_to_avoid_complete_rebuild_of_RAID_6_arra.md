---
title: "mdadm: how to avoid complete rebuild of RAID 6 array (6/8 active devices)"
date: 2008-06-25
forum: General Help
---

### Post by pbwtortilla on 2008-06-25
Hi Everyone,

First off, a little background on my setup.

Ubuntu 7.10 i386 Server (2.6.22-14-server)
upgraded to
Ubuntu 8.04 i386 Server (2.6.24-19-server)

I have 8 SATA drives connected and the drives are organized into three md RAID arrays as follows:

/dev/md1: ext3 partition mounted as /boot, composed of 8 members (RAID 1) (sda1/b1/c1/d1/e1/f1/g1/h1)
/dev/md2: ext3 partition mounted as /root, composed of 8 members (RAID 1) (sda2/b2/c2/d2/e2/f2/g2/h2)
/dev/md3: ext3 partition mounted as /mnt/raid-md3, composed of 8 members (RAID 6) (sda3/b3/c3/d3/e3/f3/g3/h3), this is the main data partition holding 2.7TiBs worth of data

All the raid member partitions are set to type "fd" (Linux RAID Autodetect).

Important Note: 6 of the drives are connected to two Sil3114 SATA controller cards whilst 2 of the drives are connected to the on-board SATA controller (I don't know which model it is).

After upgrading my Ubuntu installation to 8.04, upon system restart there was an error message saying that my RAID arrays were degraded and thus the system was unable to boot from it.

At the time, not knowing the cause of the sudden RAID failure, I attempted to force mdadm to start the arrays anyways (the RAID 1 arrays with 8 members each were no causes for concern, of course, but I wanted to back up my data on the degraded md3 array as soon as possible).

Then it hit me, why would it recognize only 6 drives? Apparently the kernel has some compatibility problems with certain SATA controllers and my on-board controller chip was one of them.

Sure enough, after moving all 8 drives to the Silicon Image controllers, the drives were all recognized without any problems.

If the missing drives were recognized again before the array was ever brought up again, everything would've been fine. But unfortunately I forced mdadm (--run switch) to bring it online with 2 missing members.

This is when the problem began. I know that as soon as I re-add the two missing drives back into the md3 (RAID 6) array, the system will attempt to rebuild the array, using the data from the 6 drives.

Given the size of the array and the type of the disk drives being used (off-the-shelf SATA drives with bit error rate of 1 out of 10^14 bits), I think it is highly likely that the system will encounter one or more bit errors during the rebuild.

Anyway, I panicked and brought the md3 array down first to prevent possible further damage.

So, at this stage what I'm wondering is:

1. If mdadm encounters a bit error during a RAID 6 rebuild, will it just give up on that particular file and move on to recover other data on the array? Or will it trash the entire array?

2. Is it possible to cheat mdadm by somehow replacing the new "raid metadata" on the 6 drives with the old data on the 2 drives? Will it make mdadm think the array is clean, consistent and nothing ever happened? Please do note that I did not write ANY new data onto the RAID 6 array from the time it was degraded until the time I brought it down with (--stop).

Sorry for the long post and thank you for your time in advance. I really hope to get this RAID array back up without data corruption because I don't have a working backup of the array (I know, very stupid of me).

Dave

---

### Post by fjgaude on 2008-06-25
All the drives are SATA, no PATAs?

I wouldn't worry about bit-error in re-building, re-sync. But **do not** use --create or --build commands whatever you do.

Your problem likely has to do with Hardy changing all hda drives to sda. But if not try:

```
sudo mdadm -D /dev/md3
```

and notice the UUID. Then we will see if all the drives have the same UUID. That way you know that --add will work without data loss.

Use the -E command to find out the UUIDs of each of the drives, which should all be the same.

---

### Post by pbwtortilla on 2008-06-25
Thank you, Frank. :)

I have resolved the problem by examining the array member order information contained in the superblocks of each of the array members, recreating the array with two missing members, and then adding the missing drives back.

Messing around with a large RAID array that does not have a backup = not fun!

---

### Post by fjgaude on 2008-06-25
Glad you got things going again, and are fully aware of the importance of full backups, two deep, like the big boys do.

Happy raiding. <smile>

---

