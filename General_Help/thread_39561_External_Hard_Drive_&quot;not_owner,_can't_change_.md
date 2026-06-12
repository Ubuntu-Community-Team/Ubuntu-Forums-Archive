---
title: "External Hard Drive &quot;not owner, can't change permissions&quot;"
date: 2005-06-05
forum: General Help
---

### Post by xbilly on 2005-06-05
"You are not the owner, so you can't change permissions"

This is the message under the "PERMISSIONS" tab in the properties menu for my External harddrive. My hard drive is connected via USB and the address is: /media/ieee1394disk

I have tried remounting and such. I want to be able to write to it and not have it just "read only".

billy

---

### Post by flanker on 2005-06-05
As long as the drive isnt formatted with NTFS then try changing the owner of the files first with the command `chown`.

---

### Post by xbilly on 2005-06-05
Tried it. it did not do anything

---

### Post by az on 2005-06-05
What filesystem is on the disk and how is it mounted?

If it is a vfat filesystem and it is mounted by the gnome-volume-manager, you should be able to write to it.  If you cannot, you should file a bug report.  bugzilla.ubuntu.com

Do you have any non-ubuntu software installed and are you running Ubuntu or Kubuntu?

---

### Post by ct_srvnt on 2005-06-05
[QUOTE=xbilly]"You are not the owner, so you can't change permissions"

This is the message under the "PERMISSIONS" tab in the properties menu for my External harddrive. My hard drive is connected via USB and the address is: /media/ieee1394disk

I have tried remounting and such. I want to be able to write to it and not have it just "read only".

billy[/QUOTE]
 Who does the "properties" tab show as being owner of the drive?  If the owner is "root" you will need to try any changes using sudo prior to the command.
I've found that the automount in Ubuntu has done some strange things with permissions in other contexts with removable media (see wordperfect thread).  You might try umounting the drive in a terminal as root (using sudo) and then manually remounting as root (also using sudo) with the appropriate permissions specified.  If this works, you might think of manually editing /etc/fstab to contain a line defining the drive with the desired permissions, simplifying the workaround in the future.

---

