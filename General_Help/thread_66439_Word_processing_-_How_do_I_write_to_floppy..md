---
title: "Word processing - How do I write to floppy.?"
date: 2005-09-17
forum: General Help
---

### Post by amclpreston on 2005-09-17
I've recently installed Ubuntu 5.04, and have just started using the word processing application.

However, when I came to save/save as what I had just typed in, I couldn't see how to write the file out to another, external drive. In this case I wanted to save the file floppy disk. I looked in the 'Help' section and it wasn't very illuminating  least to me.

A pointer please...? 

Andrew

---

### Post by Leif on 2005-09-17
in linux you need to 'mount' floppies to tell the system to use them. at the command line, type "sudo mount /dev/fd0 /media/floppy0". afterwards, you can access your floppy from /media/floppy0. when you're done using it, type "sudo umount /media/floppy0" to make sure everything has been written to the disk.

---

### Post by Irony on 2005-09-17
You can also make the floppy mount on boot-up by altering your fstab file. First back-up your present file;

*sudo cp /etc/fstab /etc/fstab_backup*

Now open the fstab file with gedit;

*sudo gedit /etc/fstab*

Alter the file so the floppy part looks like this (note don't alter the non-floppy bits as its specific to my set-up);

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hda3       /media/XPb  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/2nd  vfat    iocharset=utf8,umask=000   0       0
/dev/hda4       /media/UBb      ext3    defaults        0       0[/PHP]

I also had to enable permissions to read and write to the floppy (you may not need to do this if you can already read and write). This only takes effect on reboot;

*sudo chmod 777 /media/floppy0*

Note when I save files in say openoffice I usually prefer to save them to say desktop then drag them into the opened floppy. That way if it doesn't work you've still saved the file to desktop so it can be moved elsewhere.

---

