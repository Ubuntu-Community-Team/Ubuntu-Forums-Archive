---
title: "Drives don't want to mount"
date: 2008-05-02
forum: General Help
---

### Post by DarkDancer on 2008-05-02
I installed Hardy over the last couple days of RC and have been having some trouble getting my drives to mount. I have one pata and one sata. They used to automount when I would boot in, buit now I have to tell them to mount. If I just go into nautilus and tell them, I get this message from the Pata:

> The volume 'LDSilver' uses the EXT3 file system which is not supported by your system.

and this message from the Sata:

> Unable to mount the volume 'maarla'.and under details

> mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)

Both are ext3 drives and will mount fine if I do them with nautilus as root.

Help! (Please!) ;)


one other thing, If I try to burn a cd (k3b) it tells me that it has no permission to use the drive.

---

### Post by DarkDancer on 2008-05-02
Ok, so I got a copy of the final and reinstalled (I have some other weird issues too) no help, the exact same problem. Anyone?

---

### Post by lemming465 on 2008-05-02
Not enough information yet.  Please post the output from```
cat /etc/fstab
sudo fdisk -l
```

At a guess, the mount points are messed up.

---

### Post by DarkDancer on 2008-05-02
Ok, for cat /etc/fstab I get:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9843c115-83b8-45a4-9c9e-998d9bfd41a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a962120f-b19b-4e66-b624-717852aa6eda /home           ext3    relatime        0       2
# /dev/sda5
UUID=ebab3cbd-66e4-46d7-9a9d-36493bafd54e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


For sudo fdisk -l:

> Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002cf0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2687    21583296    7  HPFS/NTFS
/dev/sda2            2688        5298    20972857+  83  Linux
/dev/sda3            5299       48641   348152647+   5  Extended
/dev/sda5            5299        5560     2104483+  82  Linux swap / Solaris
/dev/sda6            5561        8171    20972825   83  Linux
/dev/sda7            8172       19268    89136620    7  HPFS/NTFS
/dev/sda8           19269       48641   235938591   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa876a876

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30515   245111706   83  Linux

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5aa75df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+  83  Linux


---

### Post by DarkDancer on 2008-05-03
Bump....

---

### Post by DarkDancer on 2008-05-04
Bump....

---

### Post by DaddyX3 on 2008-05-04
Sorry I don't have the time to do it for you, but this link should get you on the right track. I had a similar problem with an esata device not mounting. 
[http://ubuntuforums.org/showthread.php?p=4876760#post4876760](http://ubuntuforums.org/showthread.php?p=4876760#post4876760)

---

### Post by lemming465 on 2008-05-04
Could we also get the output of```
sudo blkid
```

---

### Post by DarkDancer on 2008-05-04
sudo blkid yielded:

> /dev/sda1: UUID="124CAAD24CAAAFC1" TYPE="ntfs" 
/dev/sda2: UUID="9843c115-83b8-45a4-9c9e-998d9bfd41a0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ebab3cbd-66e4-46d7-9a9d-36493bafd54e" 
/dev/sda6: UUID="a962120f-b19b-4e66-b624-717852aa6eda" TYPE="ext3" 
/dev/sda7: UUID="D91DEA0B4BE1DE89" LABEL="Windows Storage" TYPE="ntfs" 
/dev/sda8: UUID="a084b93e-ea9d-49e0-817d-25b7e2d7159d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="LDSilver" UUID="2a57aceb-dfb9-9520-983a-e26dbbdc4b95" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="maarla" UUID="c567bf10-ab7e-4680-ec92-fb06ed0d8029" SEC_TYPE="ext2" TYPE="ext3"

Sorry DaddyX3 couldn't figure that one out.....

---

### Post by lemming465 on 2008-05-04
I don't pretend to understand automount behaviours in gnome or ubuntu very well, so I'm not sure why they aren't automounting.  Also searching the 'net for ubuntu automount problems suggests you aren't the only one having issues, unfortunately without shedding much light on what the underlying cause might be.

One problem can be if you somehow aren't in all of the expected groups; in particular if you run *groups* from a terminal window the output should include "cdrom", "floppy", and "plugdev" among other things.  If you are still having trouble with the k3b application, check that.  Running *gksu k3b* would probably work regardless.

However, we should be able gets things mounted at boot time by listing more partitions in /etc/fstab.  Try appending lines like:

```

# /dev/sdb1
UUID=2a57aceb-dfb9-9520-983a-e26dbbdc4b95 /media/LDSilver  ext3 defaults 0 2
# /dev/sdc1
UUID=c567bf10-ab7e-4680-ec92-fb06ed0d8029 /media/maarla   ext3 defaults 0 2

```

If you want the partitions mounted somewhere else, just change the paths from /media/... to whatever you actually want, and make sure the directories exist.
You can test them by doing *sudo mount -a*

---

### Post by DarkDancer on 2008-05-04
Thanks Lemming, the drives now automount on reboot and are reachable. 

The cd's are still giving trouble though. If I gksudo k3b, it acts like it's going to work, then gives an error (255 unknown error) then won't release the cd until I reboot......

---

### Post by DarkDancer on 2008-05-06
Bump.

---

### Post by DarkDancer on 2008-05-06
Ok, never mind, this one is solved, the cd problem isn't with the cd's it's got something to do with b urning audio and that deserves it's own thread. Any way to mark this solved?

---

