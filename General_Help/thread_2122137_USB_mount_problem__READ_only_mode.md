---
title: "USB mount problem / READ only mode"
date: 2013-03-04
forum: General Help
---

### Post by morswin on 2013-03-04
Hi all,

I've got following problem: when i mount USB hard drive with "sudo mount -t vfat /dev/sdb1 /media/my_folder" usb mount in "read only" mode. How can I make it run with full permitions?

Some additonal info:
I run Xubuntu 12.10 with awesome wm;
Problem exists only when i use console, i can mount drive properly with thunar; 
Problem exists with all my fat32 flash drives (but not external ntfs HDD);
Problem is independent of window manager, i.e. it exist when i use awesome and when i switch to xfwm;
I noticed my /media dir is also read only for ordinary (not sudo) user - should it be this way? Why everything ok with HDD?

I think there's nothing wrong with usb drives, i formatted them with gparted (and they work with thunar). 

Any help will be appreciated.
Best regards,
morswin

---

### Post by sudodus on 2013-03-04
Automount at plug-in or with the file browser and check the entry in /etc/mtab. Then you can use those options in a manual mount operation (unmount, then mount).

I did this for sdd2 (while leaving sdd1 automounted)
```
sudo mount/dev/sdd2 -t auto -o rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks [COLOR=#008000]/mnt[/COLOR]
```
and got this result

```
/dev/sdd1 [COLOR=#0000ff]/media/usb-data[/COLOR] vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0
           /dev/sdd2 [COLOR=#008000]/mnt[/COLOR] vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0

```

---

### Post by schragge on 2013-03-04
To simplify things a bit, I'd install and use [pmount]("http://manpages.ubuntu.com/manpages/precise/en/man1/pmount.1.html"). It allows you to mount removable devices without sudo. It works like this:
```

pmount --noatime /dev/sdb1
[COLOR=#0000ff]# Then, when you want to unmount it[/COLOR]
pumount /dev/sdb1

```
There was once a little GUI tool named [pysdm]("http://pysdm.sourceforge.net") that helped you to write [s]/etc/fstab entries or[/s] [udev](http://manpages.ubuntu.com/manpages/precise/man7/udev.7.html) rules to automate mounting on plug-in, it's still available in precise (Ubuntu 12.04), but was removed from later releases as it uses now obsolete GTK2.

---

### Post by morswin on 2013-03-04
Thank you so much for your reply. Both worked :))

---

