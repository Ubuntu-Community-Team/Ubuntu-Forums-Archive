---
title: "[SOLVED] Could someone please help me configure my fstab?!"
date: 2008-02-16
forum: General Help
---

### Post by geo909 on 2008-02-16
Hello everybody.
I'm hitting my head on the wall with the situation here. That's what's with it:
I have a couple of USB devices.
1. A 1GB USB stick in FAT 16
2. A 256 MB MP3 Player in FAT 16
3. An external 500 GB disk in NTFS

I have also PYSDM (PYthon Storage Device Manager) to help me configure them when inserted.

But really strange things happen..
The devices do not automount, my mp3 player often opens in read-only mode ](*,)](*,)
and I can't mount/unmount them as a plain user (I need root privileges).

Could someone please help me configure my fstab file and end with this once and for all?
I need all of my devices to automount and let every user to be able to read, write, execute, mount and unmount... That's all.

Also, all of my devices are seen by Ubuntu as "sdc1". Is there a way I could configure each device to be mounted on a certain folder (for example /media/MYMP3PLAYER or /media/EXTERNALDISK) and not all of them in /media/sdc1?

Thank you very much in advance!
Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                0  0  
# /dev/sda2
UUID=5c1c4c9a-cc31-4289-96b6-ffddcc0ed8e5  /               ext3         defaults,errors=remount-ro              0  1  
# /dev/sda1
UUID=E434BA5034BA2608                      /media/sda1     ntfs         defaults,umask=007,gid=46               0  1  
# /dev/sda5
UUID=dadcfc56-ab39-4886-97dc-c26cf7bd9eee  none            swap         sw                                      0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec                        0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec                     0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,umask=000,user,uid=jorge  0  0  


/dev/sdc1                                  /media/sdc1     auto         defaults                                0  0  
```


Well it wasn't always just that line, I just tried to set the defaults..
Any ideas?

---

### Post by Stoodle on 2008-02-16
I'm not sure about them all being mounted on sdc1. However, from what I've read, don't use defaults. Change it to auto (auto-mounts), user (allows normal users to mount it), exec (allows you to execute programs), and rw (allows read-write). Of course, I'm having my own problems with it because I'm getting line 25 in /etc/fstab is bad.

This is my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/sda1 /media/Seagate\ Drive vfat auto rw,auto,user,sync umask=000 0 0

```

---

### Post by drs305 on 2008-02-16
Stoodle,

It looks like line 25 (if I counted correctly) is your seagate line. I believe "Seagate Drive" should be written like this "Seagate\Drive" without the space.

---

### Post by MighMoS on 2008-02-16
If you're using Gnome, nautilus can help you by right clicking -> properties and the drive and volume tabs allow you to set a specific mount point, mount options, etc.

---

### Post by Stoodle on 2008-02-16
Hey thanks! I think it worked!

---

### Post by Stoodle on 2008-02-16
Nevermind, it didn't.

---

### Post by geo909 on 2008-02-16
> **Stoodle said:**
> Nevermind, it didn't.

That's funny. I will answer other peoples' questions in my own thread:
I finally found the solution and its sort of ridiculous!

I just had to erase any line in fstab that didn't have to do with **permanent** storage.
I mean, no sdc1, no configuring for external devices and -voila- Ubuntu handles USB devices as I wanted! Automount, read, write, executable, mount & unmount by everybody...

The mistake was mine, I once thought I had to configure them and so it all began!

Stoodle, make a backup of your fstab file first and then remove these lines:

```
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/sda1 /media/Seagate\ Drive vfat auto rw,auto,user,sync umask=000 0 0
```

Then try to connect your external USB devices and tell me what happened..

---

### Post by dcstar on 2008-02-16
> **geo909 said:**
> Hello everybody.
I'm hitting my head on the wall with the situation here. That's what's with it:
I have a couple of USB devices.
1. A 1GB USB stick in FAT 16
2. A 256 MB MP3 Player in FAT 16
3. An external 500 GB disk in NTFS
........
Also, all of my devices are seen by Ubuntu as "sdc1". Is there a way I could configure each device to be mounted on a certain folder (for example /media/MYMP3PLAYER or /media/EXTERNALDISK) and not all of them in /media/sdc1?
.........

Simply name the partitions and they will be mounted using those names (labels).

Do a forum search for the various ways to label partitions.

---

### Post by drs305 on 2008-02-16
> **Stoodle said:**
> Nevermind, it didn't.

Sorry it didn't work. The Seagate Drive space may not be your only problem in fstab. (I'd just change it to 'seagate' to eliminate any doubt.) Anyway, you should probably start your own thread since this one is really geo909's. We can work on it there if you are still having problems.

---

### Post by geo909 on 2008-02-16
Ok, we will all be there, in the new thread to see what happens next!!

I'm setting this one as [SOLVED].

Thanks everybody for your time

---

### Post by drs305 on 2008-02-16
Well, for Stoodles sake, I'll make one more entry here.  I found a net reference that said that fstab would require the format Seagate\040Drive for the space. Learn something every night. I'd STILL change the name to seagate :???:

---

### Post by geo909 on 2008-02-17
Haha, couldn't resist to post somehing again!

Just wanted to mention that my Seagate external USB HD works fine when removing all related lines from fstab. I have a Seagate FreeAgent 500 GB USB drive..
Is your SeaGate drive similar?

Anyway, post a new thread and give a link here...

---

### Post by Stoodle on 2008-02-17
Yeah, it's a 500gb. How do you mount it then? I remember that when I first got it, I had no problems. Automounted and worked fine, no errors at all...

Here's the link.

[http://ubuntuforums.org/showthread.php?t=698950](http://ubuntuforums.org/showthread.php?t=698950)

It seems like when I try to post about multiple problems in a thread, no one likes that.

---

