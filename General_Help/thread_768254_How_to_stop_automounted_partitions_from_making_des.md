---
title: "How to stop automounted partitions from making desktop icons?"
date: 2008-04-26
forum: General Help
---

### Post by brendonbrewer on 2008-04-26
Hi everyone,

I just figured out how to make my non-primary hard disk partitions to be mounted automatically by making directories for them and editing /etc/fstab.

However, when I start up my computer, Ubuntu puts an icon for each partition on the desktop, which I don't particularly want to happen.

How can I disable this behaviour?

Thanks.

---

### Post by Vivaldi Gloria on 2008-04-26
Well, I just asked that. See

[http://ubuntuforums.org/showthread.php?p=4798584#post4798584](http://ubuntuforums.org/showthread.php?p=4798584#post4798584)

---

### Post by bollix47 on 2008-04-26
Press Alt-F2

Type - gconf-editor

Navigate to - /apps/nautilus/desktop/

Look in the right window pane for volumes_visible

Remove checkmark.

---

### Post by Naatan on 2008-04-26
I think removing the line that mounts the partition from /etc/fstab should do the trick, the desktop simply shows mounted devices.. I don't think there's an option for disabling certain devices.

---

### Post by brendonbrewer on 2008-04-26
Thanks. I'll try that soon - I just realised that I can't write to those drives :(. I did chmod a+w on their directories in /mount. Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=09099131-d1ed-4860-8193-79b69c76c24b /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=f5c38ced-d111-4e30-839a-9c60b0bdc664 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4	/media/extra    vfat	rw,auto,user	0        2
/dev/sda1	/media/vista    ntfs	ro,auto,user	0        3

---

### Post by Naatan on 2008-04-26
I'm sorry I've realized this solution is a bit to extreme as it wouldn't mount the devices all together.. you don't want that.

I did some googling and came up with this:

[http://www.linuxquestions.org/questions/debian-26/2-gnome-questions-mount-desktop-icon-and-launch-notification-274628/#post2804559](http://www.linuxquestions.org/questions/debian-26/2-gnome-questions-mount-desktop-icon-and-launch-notification-274628/#post2804559)

that should do the trick.

---

