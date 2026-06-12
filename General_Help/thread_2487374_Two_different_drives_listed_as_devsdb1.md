---
title: "Two different drives listed as /dev/sdb1"
date: 2023-06-02
forum: General Help
---

### Post by texpat on 2023-06-02
Hi and thanks for taking a look at this.

I have two drives that [FONT=Courier New]**df**[/FONT] lists as [FONT=Courier New]**/dev/sdb1**[/FONT]
Both drives are auto-mounted in fstab with their respective uuids so I can access them individually in the file system.
Is this a problem? I have a weird issue that data I rsync'd to one of the drives was gone after a reboot - over 600 GB of files from a backup. Could that be related?

I appreciate any pointers as to what to do about this.
Tx

---

### Post by ajgreeny on 2023-06-02
It is the normal way USB drives are mounted; if you attach both at the same time you will see that the first one will mount as sdb1 and the second probably as sdc1. Drive device names are given by the system according to the order of detection and mounting so can easily change from mount to mount depending on what else is already attached, which is why we should never use them in the /etc/fstab file.

The mountpoints will remain as the UUIDs of both and will never change until you format the partition.

It is a great help when formatting USB disk partitions to give each partition a Label that means something to you, easiest done using gparted as it will then automount using the label name at /media/username/label, much simpler than a long unmemorable UUID.

---

### Post by texpat on 2023-06-02
Hi ajgreeney and thanks for your input.

Only one of those drives is USB, the other an internal SATA. Both have their corresponding labels, too. My original question was, whether it is a problem that both drives are on /dev/sdb1/ and whether the disappeared data on one of the drives (the internal one) can have anything to do with this.

---

### Post by yancek on 2023-06-02
Try commenting out the two entries for these drives/partitions in /etc/fstab and manually mounting.   You might post the contents of the /etc/fstab file or at least the relevant lines so we have a clear picture.

---

### Post by texpat on 2023-06-02
```
Relevant output of df
=====================
/dev/sdb1      1921742316  635379696 1188670564  35% /hd-extra
/dev/sdd1      1953511420 1242322584  711188836  64% /media/texpat/Elements
```

Yes, I see it, too, now ...:-#

---

### Post by tea for one on 2023-06-02
> **texpat said:**
> ```

Relevant output of df
=====================
/dev/sdb1      1921742316  635379696 1188670564  35% /hd-extra
/dev/sdd1      1953511420 1242322584  711188836  64% /media/texpat/Elements
```

/dev/sdb1 and /dev/sdd1 are different.
Looks OK to me.

---

### Post by The Cog on 2023-06-02
You cannot have both drives on /dev/sdb at the same time. In post #5 I see that they are sdb1 and sdd1. 
The device IDs /dev/sd* are allocated automatically when the disk is discovered, and they are not permanent. If you remove one disk that is sdb and reconnect it, it may return as sdc or sdd. If you remove a disk that is sdb and then connect a different drive, it is possible that new one may be allocated the unused sdb identity. That would then mean that the original disk is certain to be allocated a different id once it is reconncted.
It was all much simpler when drives weren't pluggable and were always discovered in the same order. But these days you can **not** rely on disks always having the same id if you unplug and re-plug them (or reboot). 
That is why the new device entries /dev/disk/by-label, by-uuid etc were created - so you could be sure of finding the correct disk - they are all symlinks to the correct /dev/sd* device id that are linked as soon as the new disk has its properties discovered.

---

### Post by texpat on 2023-06-02
Yes, I just saw that, too. My eyes were playing tricks with me.
Please, all, accept my apologies. I can assure you I feel duly stupid now.

---

