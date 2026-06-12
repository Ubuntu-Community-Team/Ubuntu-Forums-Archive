---
title: "Places | Computer not working"
date: 2007-07-21
forum: General Help
---

### Post by cprofitt on 2007-07-21
I am having issues with using the places menu and selecting computer. The resulting File Browser then comes up with files such as 232.9%20GB%20Volume.drive. When I double click on this I get a message saying:

Couldn't display "computer:///232.9%20GB%20Volume.drive" The location is not a folder.

I am very new to Linux and Ubuntu... and searches have turned up empty.

---

### Post by dougfractal on 2007-07-21
Sounds bad.

the old way of mounting is

"ls /media"
list all the ubuntu scanned mount points


sudo mount -t ext3 /dev/hdaX /media/hdaX 

-t type   ext3,ntfs,vfat32

---

### Post by cprofitt on 2007-07-21
doug:

they are all mounted -- just that particular method of browsing is causing the issue. I can hit all the drives from the places side menu, just not from the main window.

---

### Post by dougfractal on 2007-07-21
I think it's something todo with gnome-vfs.
All I can suggest is "sudo apt-get upgrade" but I guess you are already uptodate.

So its just nautilus computer:/// 
and >Places>removable_media
but not the nautilus sidebar, which works fine.

have you edited your /etc/fstab ?

---

### Post by cprofitt on 2007-07-21
> **dougfractal said:**
> I think it's something todo with gnome-vfs.
All I can suggest is "sudo apt-get upgrade" but I guess you are already uptodate.

So its just nautilus computer:/// 
and >Places>removable_media
but not the nautilus sidebar, which works fine.

have you edited your /etc/fstab ?

Yes... I am up-to-date.
Yes... it is just nautilus computer:///
Not sure about removable_media because I have none attached
Yes... sidebar works fine

---

### Post by cprofitt on 2007-07-23
anyone?

This really concerns me and I can not find any information about what might have caused the issue.

---

### Post by cprofitt on 2007-07-23
*push*

---

### Post by cprofitt on 2007-07-24
Anyone.... at all even have a clue?

This issue concerns me to the point that I might avoid continuing to migrate to Ubuntu unless I can resolve it and figure out how to resolve it if it happens again.

---

### Post by cprofitt on 2007-08-10
Just checking back -- is there no way to fix this?

---

### Post by dougfractal on 2007-08-10
The thing is you've got a glich. You sytem is just playing up. If it only annoying, and you can still get to drive via "nautilus /media" then you may just have to go on a quest and find the answer.

But It may that gusty will fix it? Time can be the best sorter outer of troubles.

---

### Post by cprofitt on 2007-08-10
I googled...

I posted here...

After that what do you suggest? Talk to the dev team that makes Nautilus?

---

### Post by dougfractal on 2007-08-10
Lets try and lable the partitions

> ls /dev/disk/by-uuid/ -lh
cat /etc/fstab

check that the UUID match

try with one only to see if it works
> 
sudo vol_id /dev/XXXX    # each device 

> sudo e2label  /dev/XXXX [newname]  # each device

You might have to reboot

---

### Post by yorkie on 2007-08-10
have alook at this thread you might be able to remove then replace "computer" or reconfigure icon

[http://ubuntuforums.org/showthread.php?t=419031&highlight=places+menu+computer+icon+does](http://ubuntuforums.org/showthread.php?t=419031&highlight=places+menu+computer+icon+does)

---

