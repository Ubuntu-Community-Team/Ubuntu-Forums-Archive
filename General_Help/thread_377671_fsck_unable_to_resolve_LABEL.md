---
title: "fsck unable to resolve LABEL"
date: 2007-03-06
forum: General Help
---

### Post by darntson on 2007-03-06
I've seen references to my problem on the forum but I couldn't find anything specific enough -- I hope this isn't redundant.

I've been using Ubuntu for about a month so I'm still very new to the experience (and I love it, so far). I'm currently getting this error on boot:

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'LABEL=/boot'
fsck.ext3: Unable to resolve 'LABEL=/home'
fsck died with exit status 8

I didn't make any edits to fstab so I'm not sure how this started. Here is the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a7a9d9bd-950c-48ae-9288-fab271882b19 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4f993ede-b231-4082-850a-db241b4a049b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#
LABEL=/ / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
none /dev/pts devpts gid=5,mode=620 0 0
LABEL=/home /home ext3 defaults 1 2
none /proc proc defaults 0 0
none /dev/shm tmpfs defaults 0 0
/dev/hda3 swap swap defaults 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,owner,kudzu,ro 0 0
/dev/hdd4 /mnt/zip100.0 auto noauto,owner,kudzu 0 0
/dev/fd0 /mnt/floppy auto noauto,owner,kudzu 0 0

There are no other OS's on this machine either -- strictly Ubuntu.

Thanks for any assistance!

---

### Post by Malakia on 2007-03-06
I checked my fstab and I don't even have the label part in it. Here is what mine looks like.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=0c6e115c-878c-4dcc-8e56-e240534a9172 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0bf57b22-fe19-4f29-b96c-0a383f56bca7 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

What you might be able to do is comment(#) the label part out an see what happens. If it messes something up than you can just uncomment them.

---

### Post by darntson on 2007-03-06
Thanks, Malakia. I commented out the LABEL=/boot and LABEL=/home lines and it booted up just fine. Now can someone explain to me what I just disabled? :)

---

