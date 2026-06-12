---
title: "Auto-mounting HD to Desktop, How can I stop this"
date: 2008-05-16
forum: General Help
---

### Post by uclalinux on 2008-05-16
Hi, I have been using linux for some time now and I just updated to 8.04. Now every time I start up Ubuntu  auto mounts my other HD's to the desktop, Its really annoying. It never happen before I updated and I have not change my fstab. How can I prevent the auto mount to the desktop but keep the auto mount to my home as I have it in my fstab.

my fstab 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eda65ddf-ad7e-46f6-9605-bbef4b0d320b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=765fc2fb-e664-4b4b-bb2e-de9d31a5ebf0 /boot           ext2    defaults        0       2
# /dev/sda1
UUID=9644E10744E0EB47 	    /home/uclalinux/windows_partion    ntfs    defaults        0       2
# /dev/sdb1
UUID=e2cd600a-6c8e-4af5-87a7-713b020eb22d /home/uclalinux/sdb1     ext3    defaults        0       2
# /dev/sdc1
UUID=6243974e-fa2d-4c04-bfb6-437be5b1f671 /home/uclalinux/sdc1     ext3    defaults   0    2
# /dev/sda4
UUID=04f3d16e-cf8e-4fae-8124-1943e762db6d none  swap sw           0  0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 

```

---

### Post by EXCiD3 on 2008-05-16
If you want to remove the shortcuts from your desktop I would use [Ubuntu Tweak]("http://ubuntu-tweak.com/") Its a cool little app that you can easily tweak a bunch of your gnome settings without editing them in the gconf-editor.

To remove it using gconf-editor:

Press Alt-F2, and run gconf-editor. To get to the settings, navigate to /apps/nautilus/desktop and check the boxes that apply.

This just disables the icons from showing on the desktop and does not modify where the drives are mounted. :)

---

### Post by uclalinux on 2008-05-16
Thanks that works, but it also remove the icons for USB thumb drives and Ipods. I only want to remove the HD icons, the thing thats weird is the fact under mount point on the desktop icons it list the correct location .Which is /home/uclalinux/sdb1 or sdc1 , I think there is another solution to this problem.

---

### Post by EXCiD3 on 2008-05-16
I'm assuming that because they are located in fstab they are automatically given shortcuts on the desktop just like a removable drive is when it is automounted. I'm not sure how to fix that for your situation unfortunately.

---

### Post by EXCiD3 on 2008-05-16
According to this thread, Gnome displays the drives mounted in /media onto the desktop, this means that if you were to mount the drives you **didnt** want displayed to a different directory then they would not appear on the desktop. It would just be a matter of creating the folders and editing your fstab I assume.

[http://ubuntuforums.org/showthread.php?t=405870](http://ubuntuforums.org/showthread.php?t=405870)

---

### Post by uclalinux on 2008-05-16
Thank you for your persistence in this solution, I will post a solution if I find one.

---

### Post by EXCiD3 on 2008-05-16
Ok, i didnt seem to find much of anything else. If you find a solution please do post, i wouldnt mind having this myself. ;) I've sort of gotten used to having no drive icons on my desktop but i still wish i could have only the removable drives.

---

