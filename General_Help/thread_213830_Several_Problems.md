---
title: "Several Problems"
date: 2006-07-11
forum: General Help
---

### Post by Rage710 on 2006-07-11
==
1 - **Problem 1 Fixed**
==

So I installed Xubuntu (XFCE version of Ubuntu) and I cannot mount my NTFS partition. I NEED the files on there. It has all my documents for school, work, music, pictures, etc. I have tried editing my /etc/fstab

Here is a copy of that: (sudo nano /etc/fstab)
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /mnt/windows       ntfs    defults,errors=remount-ro 0

When I try to mount /dev/hda1 I get this error:
> Failed to open directory "hda1".
Permission denied.

It was originally not mounting at all, so this is a plus I guess. I now I need to get my permissions correct. Please help!
**Problem 1 Fixed**

== 
2
==
Memory, I seem to have little or none. Im currently running a 733 mhz P3 with 290 mb ram and a Trident Blade 3d. By typing "top" in terminal I have CPU using 5-10% which is normal. But memory is at 20 mb. around 14 mb free. I have no clue why this is. Its almost unusable. Im using XFCE which shouldnt use this amount...I need help. [help]

==
3
==

I have a Sony G420 monitor. (1600x1200 @ 85 hz reccomended res, but I want to use 1280x1024@ 100 hz) Im currently running 1280x1024@60 hz and I want to rip my eyes out. Ive tried looking in XORG.conf and edid it (via nano) and no luck.

Thanks in advance.

---

### Post by DrSturgeon on 2006-07-11
Problem 1:
You said you fixed it, but I'll answer anyway:  you need a umask set in the fstab for the partition.  A umask is a *mask* of a normal permissions code, and sets the default permissions for all the files on the drive.  So each number in the umask is 7 minus the number for the permission.  If you want the permissions set to 755, the umask should be 022.

So if you don't mind the partition being world readable:
/dev/hda1 /mnt/windows ntfs defults,errors=remount-ro,umask=000 0

You can also set the user and group that own the files on the partition with uid and gid:

/dev/hda1 /mnt/windows ntfs defults,errors=remount-ro,uid=youruser,umask=700 0

would make the partition readable and writable by your user only.





Problem 2:
I don't use XFCE, so I'm not exactly sure, but can you look which processes are actually using a bunch of ram?  You might have something running that you don't need.  Beagle, for example, uses a crapload of memory.




Problem 3:
The screen section in xorg.conf should look something like:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1200"
        EndSubSection
EndSection

```

Make sure you see the resolution you want (1600x1200) in the list of modes.  If it still doesn't work, xorg probably doesn't know what refresh rates your monitor is capable of at what resolutions.  Check the Monitor section of xorg.conf

---

