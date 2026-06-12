---
title: "Two hdd NTFS &quot;Move to Trash&quot; is placed only on one hdd context menu."
date: 2013-05-03
forum: General Help
---

### Post by erngab on 2013-05-03
Ubuntu 13.04

Two hdd with NTFS partitions. I use pysdm for automount.
Same adjustment on both HDD.
[http://db.tt/Oc5MJyS2](http://db.tt/Oc5MJyS2)

"HDD sdb" - with "Move to Trash" can delete with delete key, and from right click context menu ("Move to Trash" + "Delete").
[http://db.tt/WBOMBH2L](http://db.tt/WBOMBH2L)

"HDD sdc" - with no "Move to Trash" canot delet with delete key. Only can delet with right click "Delete" (no have "Move to Trash").
[http://db.tt/DuC9UTWF](http://db.tt/DuC9UTWF)

Cut, Copy, Paste work on both.

When I make synbolic link from "HDD sdc" to "Home folder", and go through "Home folder" to "HDD sdc" - "Move to Trash" is OK, placed in right click context menu, and can delet with "Delete" key. 
Regards some ideas.

---

### Post by oldfred on 2013-05-03
Generally pysdm, does not add good mount options.

Better to follow this advice, you should be able to edit current entries to match.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
> For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by Morbius1 on 2013-05-03
> **erngab said:**
> Ubuntu 13.04

Two hdd with NTFS partitions. I use pysdm for automount.
> **oldfred said:**
> Generally pysdm, does not add good mount options.
Especially since there is no pysdm in the ubuntu 13.04 repositories. ;)

---

### Post by erngab on 2013-05-04
I got "Move to Trash" and "Delete" key functionality, with this metod on all NTFS partition.


 Thanks a lot Oldfred.

---

### Post by oldfred on 2013-05-04
Thank Morbius1 as it is his post in the original thread.
Glad you got it working. :)

---

