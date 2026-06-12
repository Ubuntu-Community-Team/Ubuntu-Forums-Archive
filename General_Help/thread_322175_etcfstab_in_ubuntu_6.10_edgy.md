---
title: "/etc/fstab in ubuntu 6.10 edgy"
date: 2006-12-20
forum: General Help
---

### Post by satinet on 2006-12-20
Hi,

I am wondering how /etc/fstab works in Ubuntu 6.10.

all the entries in my /etc/fstab are actually commented out as below.

How do i change where things are mounted? And how is it mounting drives if they are commented out.....?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ddad5a1-5e88-4863-ae81-71b66b8aa7f3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ff90a48-8ed4-452e-a770-fcdcbefece8e /home           ext3    defaults,user_xattr        0       2
# /dev/sda3
UUID=dde8935f-fd91-495b-908f-647e223a8a11 /mnt/sabayon    ext3    defaults        0       2
# /dev/sda2
UUID=56eb66e4-592e-4e62-8ff4-6b33fa157000 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bionnaki on 2006-12-20
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by ciscosurfer on 2006-12-20
> **satinet said:**
> Hi,

I am wondering how /etc/fstab works in Ubuntu 6.10.

all the entries in my /etc/fstab are actually commented out as below.

How do i change where things are mounted? And how is it mounting drives if they are commented out.....?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ddad5a1-5e88-4863-ae81-71b66b8aa7f3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ff90a48-8ed4-452e-a770-fcdcbefece8e /home           ext3    defaults,user_xattr        0       2
# /dev/sda3
UUID=dde8935f-fd91-495b-908f-647e223a8a11 /mnt/sabayon    ext3    defaults        0       2
# /dev/sda2
UUID=56eb66e4-592e-4e62-8ff4-6b33fa157000 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0The lines that acutally mount your drives/partitions are not commented out, it's the lines just above them that describe the UUID they are associated with just below them that are commented out.  In other words, /dev/sda1 corresponds to  UUID=2ddad5a1-5e88-4863-ae81-71b66b8aa7f3.

This tooks some getting used to for me as well, because in Dapper and previous versions, it was not like this.  Edgy now references partitions by their UUID.

Hope this answered your question. ;)

---

### Post by satinet on 2006-12-20
ok, that's good - i thought the uuid line was so long it was on the same line as the device name, but that it was appearing on the next line!  sorry....

so if i use tune2fs -l /dev/hda1 (or dumpe2fs) i get the uuid of the device.

however, it doesn't work on /dev/hdb1 for some reason.   its mounted at /media/hdb1.

any ideas?

sudo dumpe2fs /dev/hdb1
dumpe2fs 1.39 (29-May-2006)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdb1
Couldn't find valid filesystem superblock.


anyway, i've edited /etc/fstab accordingly.  sorry for the dumb question.

---

### Post by ciscosurfer on 2006-12-20
> **satinet said:**
> ok, that's good - i thought the uuid line was so long it was on the same line as the device name, but that it was appearing on the next line!  sorry....

so if i use tune2fs -l /dev/hda1 (or dumpe2fs) i get the uuid of the device.

however, it doesn't work on /dev/hdb1 for some reason.   its mounted at /media/hdb1.

any ideas?

sudo dumpe2fs /dev/hdb1
dumpe2fs 1.39 (29-May-2006)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdb1
Couldn't find valid filesystem superblock.


anyway, i've edited /etc/fstab accordingly.  sorry for the dumb question.The following code, entered in a Terminal, will show you the relationships between your disks and their respective UUID's.  You can then use the information that's gleaned from the output to make /dev/hdb1 mount at startup via an entry in your /etc/fstab (what sort of filesystem resides on that disk, btw? (ext3, ntfs, fat32, etc.))```
ls -l /dev/disk/by-uuid/
```By the way, I believe you can substitude the old style of mounting for the UUID if you like (it should work just fine).  In other words, instead of an entry like:```
# /dev/sda1
UUID=2ddad5a1-5e88-4863-ae81-71b66b8aa7f3       /      ext3    defaults,errors=remount-ro 0       1
```You could use instead```

/dev/sda1       /      ext3    defaults,errors=remount-ro 0       1
```I'm not completely positive on how this effects Edgy, but I believe it should work.  I'll do some more research and get back to you if things are different.

PS You may find [this link]("http://en.wikipedia.org/wiki/UUID") interesting as well :-)

EDIT: 
[This thread is fantastic]("http://www.ubuntuforums.org/showthread.php?&t=283131")

The command **blkid** will also list your devices by UUID (but I don't know if it only reads-in your /etc/fstab, which obviously means if there are other drives that haven't been placed there yet, they may not show up)

[Another thread of interest]("http://ubuntuforums.org/showthread.php?t=286758") (and apparently, you can still use the "old" form to mount your disks (that is, calling it via it's device name and not it's UUID)

[Interesting post here]("http://ubuntuforums.org/showpost.php?p=1907745&postcount=4")

[Last one, I promise]("http://ubuntuforums.org/showthread.php?t=223182&highlight=UUID") :-)

---

### Post by satinet on 2006-12-22
thanks for your interesting post.

I am wondering what the reason behind this change is.  As a retired unix admin these changes take me a bit by surprise (cue misty flash back of hp-ux racks.... well it was only 6 months ago....).

What's the reason behind it?

although I guess it does make some sense - partitions can changed their /dev/ name if you edit some other partitions. I guess if you had 3 extended partitons - /dev/sda5,6,7 and you merged 5 and 6 into one, /dev/sda7 would get screwed up in your /etc/fstab file....

---

### Post by mcduck on 2006-12-22
> **satinet said:**
> 
What's the reason behind it?

although I guess it does make some sense - partitions can changed their /dev/ name if you edit some other partitions. I guess if you had 3 extended partitons - /dev/sda5,6,7 and you merged 5 and 6 into one, /dev/sda7 would get screwed up in your /etc/fstab file....

Yes, that's the reason for using UUID's. Also portable hard drives change their dev number depending on which order you plug them in, so you can't really make entries for them in fstab with dev numbers. But with UUID's there's no problem.

---

### Post by bodhi.zazen on 2006-12-22
> **mcduck said:**
> Yes, that's the reason for using UUID's. Also portable hard drives change their dev number depending on which order you plug them in, so you can't really make entries for them in fstab with dev numbers. But with UUID's there's no problem.

FYI: You can mount portable devices by label:

LABEL=<u_name_it> /mount/point

However, this has not gone so smooth in Feisty :(

On the other hand I have not looked in to it much.

=================

Helpful commands:

ls /dev/disk/by-label -l

ls /dev/disk/by-uuid -l

---

### Post by izmeh on 2006-12-22
Hey, I've been trying to get read access to the ntfs partion on my sata drive with the old & new format. Both resulted in a "wrong fs type"

i followed the guide [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows") for both dapper and edgy. It worked fine in dapper, yet gives me an error in edgy.

Here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fb6ff4a7-ea43-4a57-b31f-fe1728322486 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=194fc7b6-6614-4595-bcea-7c9cd686c39d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda1
UUID=C85C3A4D5C3A3712	/windows	ntfs	nls=utf8,unmask=0222 0 0
```

this is the error i get 
```
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/C85C3A4D5C3A3712,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by bodhi.zazen on 2006-12-22
You need ntfs-3g for read write access.

[ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g)

---

