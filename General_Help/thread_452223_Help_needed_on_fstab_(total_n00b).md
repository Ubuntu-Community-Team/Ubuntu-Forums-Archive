---
title: "Help needed on fstab (total n00b)"
date: 2007-05-23
forum: General Help
---

### Post by knappy on 2007-05-23
as stated in the title, I'm a total Linux n00b.  I'm having a weird issue.  Everything worked fine, I left the house for a bit, and my little brother got on the computer, now all hell has broke loose.

Okay, background.  

Dual boot Ubuntu 7.04 and Windows XP.  Separate hard drives etc.

So heres the problem.

My XP hard drive was showing up in Ubuntu.  I was able to mount it, copy files to and from, etc etc.

now, each time I boot up, I get an error message that reads....

```
[mtent]: line 12 in /etc/fstab is bad
[mtent]: line 15 in /etc/fstab is bad
```

here's my fstab.  


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         default$
# /dev/hdb1
UUID=283e31ac-c399-4839-a604-815bb41216c8  /               ext3         default$
# /dev/hdb5
UUID=550a10d1-f68f-4867-a63d-0c0f97d95f51  none            swap         sw     $
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,no$
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,no$
/dev/fd0                                   /media/floppy0  auto         rw,user$
/dev/hda4                                  /media/All Your Base  ntfs         n$
/dev/hdb1                                  /media/hdb1     ext3         default$
/dev/hdb5                                  /media/hdb5     swap         sw     $
/dev/hda4                                  /media/All Your Base  ntfs         n$
/dev/hda4                                  /media/hda4     ntfs         default$
```

Now I'd like to be able to access it again and etc, so any and all help would be greatly appreciated.  Thank you in advance.

---

### Post by Famicommie on 2007-05-23
Why do you have three entries for hda4?

Also, I am not an fstab expert, but linux generally doesn't like spaces in file/directory names. From a terminal, a folder named "All Your Base" would appear as "/media/All\ Your\ Base/" With the backslash preceeding each space. That is possibly the cause of your issue, though I am not sure if you would have to use the backslases for proper console notation or if simply using quotation marks would suffice. Make a backup of your fstab ```
sudo cp /etc/fstab /etc/fstab.bak
``` before you decide to do any tinkering, though.

---

### Post by knappy on 2007-05-23
I've got absolutely no idea why there are the three entries....

so, from what I gather things should look more like this correct?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         default$
# /dev/hdb1
UUID=283e31ac-c399-4839-a604-815bb41216c8  /               ext3         default$
# /dev/hdb5
UUID=550a10d1-f68f-4867-a63d-0c0f97d95f51  none            swap         sw     $
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,no$
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,no$
/dev/fd0                                   /media/floppy0  auto         rw,user$
/dev/hda4                                  /media/All\ Your\ Base/ ntfs         n$
/dev/hdb1                                  /media/hdb1     ext3         default$
/dev/hdb5                                  /media/hdb5     swap         sw     $
/dev/hda4                                  /media/All\ Your\ Base/  ntfs         n$
/dev/hda4                                  /media/hda4     ntfs         default$
```

---

### Post by knappy on 2007-05-23
sorry, please delete this post

---

### Post by shad0w_walker on 2007-05-23
It shouldnt have the trailing slash on it but apart from that it looks good, try this:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         default$
# /dev/hdb1
UUID=283e31ac-c399-4839-a604-815bb41216c8  /               ext3         default$
# /dev/hdb5
UUID=550a10d1-f68f-4867-a63d-0c0f97d95f51  none            swap         sw     $
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,no$
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,no$
/dev/fd0                                   /media/floppy0  auto         rw,user$
/dev/hda4                                  /media/All\ Your\ Base ntfs         n$
/dev/hdb1                                  /media/hdb1     ext3         default$
/dev/hdb5                                  /media/hdb5     swap         sw     $
/dev/hda4                                  /media/All\ Your\ Base  ntfs         n$
/dev/hda4                                  /media/hda4     ntfs         default$
```

---

### Post by knappy on 2007-05-23
> **shad0w_walker said:**
> It shouldnt have the trailing slash on it but apart from that it looks good, try this:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         default$
# /dev/hdb1
UUID=283e31ac-c399-4839-a604-815bb41216c8  /               ext3         default$
# /dev/hdb5
UUID=550a10d1-f68f-4867-a63d-0c0f97d95f51  none            swap         sw     $
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,no$
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,no$
/dev/fd0                                   /media/floppy0  auto         rw,user$
/dev/hda4                                  /media/All\ Your\ Base ntfs         n$
/dev/hdb1                                  /media/hdb1     ext3         default$
/dev/hdb5                                  /media/hdb5     swap         sw     $
/dev/hda4                                  /media/All\ Your\ Base  ntfs         n$
/dev/hda4                                  /media/hda4     ntfs         default$
```

With that I get

```
[mntent]: line 8 in /etc/fstab is bad
[mtent]: line 12 in /etc/fstab is bad
[mtent]: line 14 in /etc/fstab is bad
[mtent]: line 15 in /etc/fstab is bad
mount: can't find /media/All\ in /etc/fstab or /etc/mtab
```

---

### Post by fanatik on 2007-05-23
comment out (ie put a # at the start) any duplicate lines - they are not required. so in this case remove the last 2 lines. also you appear to have a duplicated line for /dev/hdb5, so comment this out too.

then run sudo fdisk -l and paste the output of that - we can then use this to correlate what you should have.

your windows partition most probably should be mounted at /media/windows - i suspect thats one of the things your brother renamed!

---

### Post by knappy on 2007-05-23
I got it fixed.  Done some tinkering, and kept re-doing it.   And I found out how he messed it up.   He installed a package entitled "Storage Device Manager" for redhat.  Thus why everything was way wonky.  I actually figured out most of the fstab by booting from the cd and checking out the cd fstab.  This is the result, and all is working fine now. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=b13fbb5c-6b62-4972-9cfc-60cff44e0e27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=6b183dba-a412-4fef-89ad-16a3ce72d8d6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Now, I do have one other question, is there a way to permantly mount said drive?  If not oh well, it's not like it's hard to mount it each time I restart or anything.

---

### Post by Famicommie on 2007-05-24
Yes, it is possible to get your Windows drive to mount on boot. You have to add it to your fstab *properly*.

First, make a mount point without spaces in the name
```
sudo mkdir /media/windows
```

Then, you need to open your fstab and make the appropriate changes. My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0

```

Your last line will have /dev/hda4 as the file system, /media/windows as the mount point, ntfs as the type, etc.

---

### Post by knappy on 2007-05-24
Thanks Famicommie.  That worked out just fine.  

Thanks to all for helping this n00b out.  This is my first true experience with any form of Linux (although I have used unix, very extensively at one point).  So far, I'm finding Ubuntu very very user friendly, unlike all the nightmare stories I've heard in the past.

---

