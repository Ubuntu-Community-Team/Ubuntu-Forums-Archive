---
title: "Can't auto-mount HD"
date: 2016-07-04
forum: General Help
---

### Post by roma24ster on 2016-07-04
I am trying to set it up so the ext4 partition of my external HD mounts automatically when I boot the computer. 

I was using the 'disks' utility to set this up, but I borked it somehow. [Here are my options selected in 'utility']("https://drive.google.com/open?id=0B7vudxstRQ__UDdnV2h0Ym5qZkE"), when I turn off automatic mount options (and therefore turn on the options in the screen shot) I get the following error: 

```

Error mounting system-managed device /dev/sda2: Command-line `mount "/media/fa7e62a0-92d8-4af6-86d9-bdf5a38e786a"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

When I turn automatic mount options on (and therefore turn the options in the screen shot off) the partition mounts fine.

Can someone help me to automatically mount the partition on system boot?

Edit:


```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006d9d9


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   524646399   262322176    7  HPFS/NTFS/exFAT
/dev/sda2       524646400  1953523711   714438656   83  Linux


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb2e551a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2   *      206848   206723071   103258112    7  HPFS/NTFS/exFAT
/dev/sdb3       206725118   976771071   385022977    5  Extended
/dev/sdb5       206725120   903045119   348160000   83  Linux
/dev/sdb6       934791168   966535308    15872070+  83  Linux
/dev/sdb7       966537216   976771071     5116928   82  Linux swap / Solaris
/dev/sdb8       903047168   934789119    15870976   83  Linux


Partition table entries are not in disk order
jamie@jamie-ncase:~/Downloads$
```

---

### Post by Dennis N on 2016-07-04
I automatically mount a Linux partition on another drive by simply adding 2 lines to the bottom of /etc/fstab of the Linux OS I am booting. 

Example: (the first line is just a comment)
```
# Label=Common-Files at /dev/sdb1
UUID=8395cc9b-002c-4af5-9c49-e5908e4ede74 /mnt/Common-Files ext4 defaults 0 2

```
Get the UUID of the file system you are mounting from sudo blkid.
Using this, sdb1 is mounted at /mnt/Common-Files when my Linux OS starts.
Common-Files was a label I gave the file system on sdb1 when it was created for easy recognition. I used the same for the mount point folder /mnt/Common-Files.

---

### Post by roma24ster on 2016-07-04
Thanks that seems to work really well!

---

### Post by Dennis N on 2016-07-04
Just in case you might not know, in order to use that newly created partition (write data to it), you need to change the owner of the mount point to your user name:

If your user name is mary, then:
```
sudo chown -R mary:mary /mnt/Common-Files
```

Then you have full access.

---

