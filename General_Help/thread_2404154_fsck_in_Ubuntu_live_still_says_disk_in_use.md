---
title: "fsck in Ubuntu live still says disk in use"
date: 2018-10-20
forum: General Help
---

### Post by rob190 on 2018-10-20
Hi,

I'm trying to fix a failed upgrade to 18.04 and I need to check the disk isn't corrupted. I'm now running 18.04 using Ubuntu live but when I try 'fsck /dev/sdb' (the boot + swap disk), it says '/dev/sdb/' in use. Cannot continue, aborting. The advice in all the forums is to use a live CD so what am I doing wrong?

Rob.

---

### Post by ajgreeny on 2018-10-20
Let's see a screenshot of the disk using gparted on the live system.

It is probably the swap partition if you have one that is detected and used by default when you boot a live system.

However, you do not run fsck on a device eg /dev/sdb, but on the partition, eg /dev/sdb1.  We need to know the partitions you have to be able to tell you more detail, so from the live system also show us the output of ```
sudo parted -l
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by rob190 on 2018-10-20
Thanks. Yes I was specifying the disk rather than the partition. I can now get a sensible output from the boot partition although it completes suspiciously quickly. I guess I'm used to disk checks taking minutes. Is it supposed to be instantaneous? Also 'fsck' by itself is supposed to check everything according to the documentation but just returns without any info or error. Same thing when I try the swap partition.

Unfortunately getting screenshots or outputs is rather difficult. From the terminal, all I get is:

```

robert@XXX:~$ sudo gparted -l                                                
Unit -.mount does not exist, proceeding anyway.
robert@XXX:~$ (gpartedbin:2521): Gtk-WARNING **: 23:33:31.023: cannot open display:

```

(This is the problem I'm trying to debug.)

From Ubuntu live, I get a list of all the disk partitions but I don't have an easy way to take a screen shot.

---

### Post by SeijiSensei on 2018-10-20
The OS will look to see if the disk was closed properly and mark it clean if so.  In that case fsck will not actually scan the disk.  

If you want to force a scan, use
```
sudo e2fsck -f /dev/sdb1
```

If you see blocks coming up bad, you can use the -c option along with -f to invoke the "badblocks" program during the scan.  It will mark such blocks and not use them when formatting the drive.  This can add hours though.

See "[man e2fsck]("https://linux.die.net/man/8/e2fsck")" for full details on this program.

---

### Post by ajgreeny on 2018-10-21
The command I said to run was ```
sudo parted -l
```, not ```
sudo gparted -l
``` which would have shown us the partitions on your system and given more info on where to go from here.

It will still be worth trying this before deciding on the next move.

---

