---
title: "Photoshop Wine device permissions"
date: 2008-02-19
forum: General Help
---

### Post by superyounan1 on 2008-02-19
So you're supposed to see an error as you try activating it saying that you don't have enough space on the hard disk. I found a site ([http://blog.crowdway.com/2008/01/26/how-to-photoshop-cs20-on-ubuntu-gutsy/](http://blog.crowdway.com/2008/01/26/how-to-photoshop-cs20-on-ubuntu-gutsy/))  that suggestst you need increase the read/write permissions on your primary drive device:

```
chmod a+wr /dev/hda
```

or whatever device your root partition is on. Then you run the activation, when you're done you reset it back by doing 

```
chmod a-wr /dev/hda
```

Well I did that, and it did not work, so I started doing the same for my other devices until I hit the right one (didn't occur to me to check my fstab yet). I ended up messing with  hda1, hda2, hda5, sda, each time trying the photoshop activation until i find whichever one must be my root device, but failed each time.

Now i have 2 problems:

1) first and most importantly, I'm not sure what the default permissions were for each of these. I *THINK* I put them all back to what they were, but I'm not positive:

```
ls -l /dev/hda /dev/hda1 /dev/hda2 /dev/hda5 /dev/sda
brw-rw---- 1 root disk    3, 0 2008-02-18 01:38 /dev/hda
brw-rw---- 1 root disk    3, 1 2008-02-18 01:38 /dev/hda1
brw-rw---- 1 root disk    3, 2 2008-02-18 01:38 /dev/hda2
brw-rw---- 1 root disk    3, 5 2008-02-18 01:38 /dev/hda5
brw-rw---- 1 root plugdev 8, 0 2008-02-18 07:38 /dev/sda

```

(2 hard disks, multiple partitions on each)

I would appreciate it if somone verified these are all correct, most espcially for my root partition's device, I don't want to lock myself out of my own hard drive or to leave the door open for security vulnerabilities.

2) the photoshop activation error still shows up, assuming the instructions on the site are correct, I must not have found my root partition's device. Based on my fstab though, it should be **hdb2**, right? If that sounds right to you, please chime in, that way I can figure out if the elevating the permissions is not doing the trick like it says on that site:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=f1e4585d-9455-490a-b7be-42f45c06d7e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=62803B24803AFE5B /media/hda1     ntfs    defaults,umask=000,gid=46 0       1
# /dev/hda5
UUID=60E8E2F3E8E2C67E /media/hda5     ntfs    defaults,umask=000,gid=46 0       1
# /dev/hdb1
UUID=8A30F85230F8472B /media/hdb1     ntfs    defaults,umask=000,gid=46 0       1
# /dev/hdb3
UUID=172f1454-38d9-4ba9-9b38-d204e140e137 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

THANK YOU IN ADVANCE

---

### Post by pointone on 2008-02-19
The files in /dev are regenerated/reconfigured on boot, if I recall correctly, but regardless, your permissions do look fine.

And yes, according to your fstab, /dev/hdb2 is your root partition.

I don't know why the fix isn't working for you, though.

---

