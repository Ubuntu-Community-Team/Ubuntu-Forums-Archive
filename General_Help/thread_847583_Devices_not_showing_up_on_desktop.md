---
title: "Devices not showing up on desktop"
date: 2008-07-02
forum: General Help
---

### Post by Kenchu on 2008-07-02
None of my devices will show up on my desktop. However, they do show up in the Places menu at the top. If I click one of them, then that particular device will be added to the desktop, though it will not be opened. I'd have to click on it again to do that.

This is annoying. Any ideas why it is like this?

---

### Post by soccerboy on 2008-07-02
what is the output of ```
cat /etc/fstab
```?

---

### Post by Kenchu on 2008-08-18
:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=550065f1-f48a-41bd-aad5-b671bbe5d50d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4fe90ec9-e085-41dd-a95f-9a0900c559ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by mb_webguy on 2008-08-18
Try installing the Gnome Configuration Editor ("sudo apt-get install gconf-config").  Open the Gnome Configuration Editor and navigate to apps->nautilus->desktop and make sure volumes_visible is checked.

---

### Post by Kenchu on 2008-08-19
gconf-editor was the only thing I could find, but I guess that is what you meant.

volumes_visible is checked.

---

### Post by dexter.deepak on 2008-08-19
i think you are facing a problem of auto-mounting your drives on startup, rather than just showing them on desktop ...right ?

---

### Post by Kenchu on 2008-08-19
> **dexter.deepak said:**
> i think you are facing a problem of auto-mounting your drives on startup, rather than just showing them on desktop ...right ?

Im not sure if I got this right, but I can access the devices. They're just not showing up on the desktop until I click them in the places menu.

---

