---
title: "link"
date: 2007-08-21
forum: General Help
---

### Post by Imsati on 2007-08-21
I finally gave Ubuntu 7.04 a shot and installed it last night. I still don't like the KDE version, but Gnome is very nice so far. Much easier to get things installed and up to speed than Dapper. I still prefer Dapper, but I'll see how the Fawn grows on me.

Anyway, I digress... How do I link at item to my Desktop? I Mounted my Shared Linux and my Personal XP partitions and they show up under Filesystems in Root, but when I try to move them to the Desktop, it tells me that they are too large to place there. Is there a way to create a link on the Desktop?

Thanks!
--Jay

---

### Post by LuckyDevil on 2007-08-21
Where did you mount them?  If you mount under /media/ they will automatically show up on your desktop, I believe.

Can you post your /etc/fstab ?  That would help.

Thanks

---

### Post by Imsati on 2007-08-21
Well, my Personal XP partition was mounted as /JasonXP

Kubuntu Root is under /KRoot; and Kubuntu Home is under /KHome.

Can I move them to Media after the fact?

I'd really love for them to show up on the Desktop and if a re-install is the only way, I'd rather do it now since I'm not even fully customized yet with all my settings.

---

### Post by Imsati on 2007-08-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=18665a3c-30aa-4b8a-bcc1-920716ca4ee8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=BF1D-80C8  /JasonLinux     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=AC14C58414C5524E /JasonXP        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=cc84edcb-6a5a-41dc-9dbe-0909746f5b3c /KHome          ext3    defaults        0       2
# /dev/sdb7
UUID=c5799487-be2c-47db-8474-c8f86ef99b00 /KRoot          ext3    defaults        0       2
# /dev/sdb6
UUID=e2be7684-ca0b-43e2-932a-a6db7230688d /home           ext3    defaults        0       2
# /dev/sda1
UUID=240CCDE80CCDB558 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2C50944A50941CA0 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=b6d54103-1e7e-40d6-ac9b-de29e717d4a3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by LuckyDevil on 2007-08-21
Nope...no re-install necessary.

If you post your /etc/fstab I can give your some "hopefully" very good specifics.  But you just need to change the mount point...
[edit]sorry, just saw you posted it[/edit]

If your kubuntu root partition is at /dev/sda1 for instance, your fstab should have

/dev/sda1    /media/kubuntu_root    ext3     defaults   0    2

The options are personal preference, that would give the user read/write access...up to you.

You would also need to create this directory 
cd /media
sudo mkdir kubuntu_root   <- or whatever you want it to be called

You would just do the same for each partition you want wanted (obviously the options are different for ntfs).

So create directories for your kubuntu root, home, and your windows inside media...then have fstab mount to those directories.

After you do that...you can unmount and remount to ensure it worked
sudo umount -a
sudo mount -a

Sorry for the long-winded reply. :-)

---

### Post by LuckyDevil on 2007-08-21
> **Imsati said:**
> # /etc/fstab: static file system information.

UUID=AC14C58414C5524E /JasonXP        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=cc84edcb-6a5a-41dc-9dbe-0909746f5b3c /KHome          ext3    defaults        0       2
# /dev/sdb7
UUID=c5799487-be2c-47db-8474-c8f86ef99b00 /KRoot          ext3    defaults        0       2
# /dev/sdb6



So those are three you're looking for, kubuntu root, home, and your windows, correct?

First, create the directories...
cd /media
sudo mkdir winXP
sudo mkdir kubuntu_root
sudo mkdir kununtu_home

Just change the mount points in fstab, so you have
UUID=AC14C58414C5524E          /media/winXP       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
UUID=cc84edcb-6a5a-41dc-9dbe-0909746f5b3c         /media/kubuntu_home     ext3    defaults        0       2
UUID=c5799487-be2c-47db-8474-c8f86ef99b00             /media/kubuntu_root     ext3    defaults        0       2


Then just unmount and remount - (just for info, these commands unmount and remount everything in fstab)
sudo umount -a
sudo mount -a

Hope that helps!

---

### Post by Imsati on 2007-08-21
well, I successfully made the directories, but when I tried to move the JasonXP over, it said there wasn't enough space.

Oh well. Seeing as how this will be my first real experience with 7.04 I'm sure I'll tweak something or play with something I shouldn't be fooling with and require a re-install anyway. Not putting myself down, but it's just how I learn stuff. I can live with things the way they are until then. I'll play around with it a bit later (Need to take care of some stuff now) and see if I can figure it out a bit more. Thanks so much for your help! I really appreciate it!

--Jay

---

### Post by LuckyDevil on 2007-08-21
No problem.

If I could ask, when does it say there wasn't enough space?

You're not moving anything here.  You're changing the mount point...you shouldn't be using the mv command at all.  You unmount it from /JasonXP and mount it at /media/winXP.  When you see the files at /JasonXP...that is a mount to the physical partition of /dev/sdb3.  The files are not "physically" on your root partition ( / ), if that makes sense.  Possibly somebody else could explain more clearly?

```

sudo umount /dev/sdb3
cd /media
sudo mkdir winXP
sudo mount -t ntfs /media/winXP

```

But if you're fine the way it is, that's good too.  :-)

> 
I'm sure I'll tweak something or play with something I shouldn't be fooling with and require a re-install anyway. Not putting myself down, but it's just how I learn stuff.


Cheers.  That's certainly how I learned all I know of linux, that and man pages.
Rich

---

