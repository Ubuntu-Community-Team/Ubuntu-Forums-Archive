---
title: "Help!! Need to recover data!!!"
date: 2007-05-10
forum: General Help
---

### Post by nick_533 on 2007-05-10
Hi all,

I am a novice with ubuntu..and just installed it on my laptop. I had two partions on my pc, 1.) 10gb C:\ where winodws works   and  2.) 20gb D:\ where I had some important files in 10gb , and the remaining 10gb was free.

I  chose auto-partition option, and Ubuntu partioned the D:\ into two parts  It installed on the free 10gb on D:\ but the other 10gb which had my files got hidden. I can not access it from windows or ubuntu.

I would really appreciate if you could tell me a way to view this hidden 10gb.

---

### Post by Zelutos on 2007-05-10
I have aquired a disk called 'The Ultimate boot disk for windows' which has some very good file recovery software. If you google that you might be able to find something about how to get it.

---

### Post by arkangel on 2007-05-10
Dont panic most probably your data is intact , but not properly mounted, if mounted at all 

open a terminal  and 

> $ sudo fdisk  /dev/**hda**

well  most probably, again, **hda** or if sata  something like **sda**

and press p. This will print  how is your partition table.  In this menu you will see how is called your missing part; example /dev/hda5.   Once you know this exit from fdisk(be careful  do not edit nothing here just see )  

Next,  create  a directory in /media (default point for mounting )

> $ sudo  mkdir /media/harddisk   
  
or someting similar, then mount it
 
> $ sudo mount -t type  /dev/hda5 /media/harddisk

where **type**  is **vfat** for a fat32 file system and** ntfs** for the ntfs file system (this is also given by fdisk ).

For more info about mounting and unmounting manually, as well another selected topics , go here  [wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") 

tell us how it is going :)

---

