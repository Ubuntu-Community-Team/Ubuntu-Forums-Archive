---
title: "USB External Hard Drive Trouble"
date: 2008-05-23
forum: General Help
---

### Post by skippynumnums on 2008-05-23
Hey, I'm pretty new to Ubuntu and I'm trying to use my "My Book Office Addition USB 2.0 500GB External Hard Drive." When I go to the "My Computer" section the two partitions I have on it show up, but I can't download files from Firefox to the Hard Drive. It doesn't show up as a download location. One of the partitions is NTFS and the other is FAT32(I think) Please Help!!!

PS - One thing I noticed was that they are both read only, but it wouldn't let me change it to read and write.

---

### Post by skippynumnums on 2008-05-24
Hey... so I use some other programs and none of them recognize that I even have an external hard drive attached except for "Movie Player" which will let me watch movies off of my external hard drive... PLEASE... HELP ME!!!

---

### Post by skippynumnums on 2008-05-24
Ok... So I actually figured if out for myself. For some odd reason the external hard drive does not appear next to "File System" and "Desktop" in most programs like it does in the "Places" tab. Instead it is located at "File System/media." So just open the media folder and your hard drive should be somewhere in there. This may seem obvious to a faithful linux user, but, for those of us who are used to Windows, it can be pretty confusing.

TTYL,
Skippy

---

### Post by |Eric| on 2008-05-25
yep 

Explanaition

basicaly in windows each drives has a root & windows assign a letter to each root (drive/partitions) 

in linux there is only one root (shown as Filesystem in ubuntu but its real name is "/" every other file/drives are mounted under that root 

ubuntu will link some of the medias that are mounted under the root 
& show them as separate drives like in windows but that somtimes isnt happening for some reason you can unload the media wait a min or two the reload it icon should become mapped


in ubuntu media are loaded/monted under /media/device_name in other linux distros its under /mnt/device_name


if your media isnt mounted you can open a terminal & write at the prompt# mount /dev/(device_filename ie sda?,sd??) /mnt/(devicenamefolder)

---

