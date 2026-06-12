---
title: "Dual Boot"
date: 2008-05-19
forum: General Help
---

### Post by boyce1 on 2008-05-19
I know you can use wubi to install Ubuntu as a regular windows application, but is there yet a way to install windows in a linux based pc?

i have linux, and now want to dual boot with windows due to some software that i need to use thats unsupported through wine.

is the only way to partition and do a manual dual boot, meaning i would have to format my linux?

is there a way to partition my hardrive, but still keep the linux OS intact without screwing up my current ubuntu?

Also, is there any software like acronis where i can save an image of my current OS? And if there was, could I just do a manual partition edit and install both OS's, then restore the Linux using the image?

thanks

---

### Post by cdtech on 2008-05-19
It used to be that Window's was fussy about being the primary OS, not sure but I think you have to have windows installed first and use a partition for Ubuntu.

---

### Post by knutschr on 2008-05-19
Look here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Bakon Jarser on 2008-05-19
> **boyce1 said:**
> I know you can use wubi to install Ubuntu as a regular windows application, but is there yet a way to install windows in a linux based pc?

i have linux, and now want to dual boot with windows due to some software that i need to use thats unsupported through wine.

is the only way to partition and do a manual dual boot, meaning i would have to format my linux?

is there a way to partition my hardrive, but still keep the linux OS intact without screwing up my current ubuntu?

Also, is there any software like acronis where i can save an image of my current OS? And if there was, could I just do a manual partition edit and install both OS's, then restore the Linux using the image?

thanks

You could try using a VM to install windows and see if you can run your programs that way.  Here is a link to the wiki.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

For saving an image of your current OS I think this might be what you're looking for.

[http://ubuntuforums.org/showthread.php?t=688872&highlight=make+live+cd](http://ubuntuforums.org/showthread.php?t=688872&highlight=make+live+cd)

---

### Post by mikewhatever on 2008-05-19
You shouldn't need to format any of the existing partitions to install Windows. Resize one of them to free up space with Gparted live CD, then create a partition for Windows. Use Clonezilla to image Linux or Windows.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.clonezilla.org/](http://www.clonezilla.org/)

The only thing to worry about would be the bootloader. Windows will overwrite Grub from the MBR and you'll need to restore it. It's a good idea to backup the current menu.lst before installing.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by boyce1 on 2008-05-19
:s that all looks quite messy and complicated...

is this the easiest way to do it? o.0

---

### Post by boyce1 on 2008-05-20
i tried to use clonezilla to burn an image of my hardrive,
but just before the actual burn process it says that it can only burn unmounted harddrives. how would i unmount my only drive to enable a disk burn?

---

### Post by Bakon Jarser on 2008-05-21
> **boyce1 said:**
> i tried to use clonezilla to burn an image of my hardrive,
but just before the actual burn process it says that it can only burn unmounted harddrives. how would i unmount my only drive to enable a disk burn?

I don't know but I'm pretty sure you don't have to do that to use remastersys.

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

