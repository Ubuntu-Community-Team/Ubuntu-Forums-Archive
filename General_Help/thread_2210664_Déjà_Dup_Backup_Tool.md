---
title: "Déjà Dup Backup Tool"
date: 2014-03-12
forum: General Help
---

### Post by mmcl26554 on 2014-03-12
I would like to have Déjà Dup Backup Tool put the backup file on my network drive, but I cannot figure out how to set it to do that.   Or is it not possible?  Can someone tell me if it is possible and how to do it.
Michael

UPDATE:
Hooray! I figured it out on my own!

---

### Post by Bucky Ball on 2014-03-12
Would you care to share? As the thread is marked 'solved' others will find it in hopes of a fix. ;)

---

### Post by mmcl26554 on 2014-03-12
Here is what I did. 
To find out the location address of my network drive I first mounted it, then I hovered my cursor over it in the list which can be seen when you click on the Home folder from the left side of my desktop.   This gave me the address which is smb://Raspberrypi/usbdrive1/   In Deja Dup I selected "Custom location" and entered the address smb://smb://Raspberrypi/usbdrive1/,  then I added the additional location where I wanted the file to be  linux/ubuntu/ubuntubackups/.   So the entire address it smb://Raspberrypi/usbdrive1/linux/ubuntu/ubuntubackups/.    I then was able to do the backup to that file.     The only thing that was strange was that the file /linux/ubuntu/ was already on the drive and I had intended for Deja Dup to just add /ubuntubacups/ to the folder but it made an additional folder so now I have two folders named "Linux/ubuntu" on the network drive.     I don't quite understand why it didn't use the folder that was already there but that isn't a big problem for me.   But the lack of understanding is because I am a Linux beginner with a lot to learn.   But it's a good exercise for my old brain.
Michael

---

