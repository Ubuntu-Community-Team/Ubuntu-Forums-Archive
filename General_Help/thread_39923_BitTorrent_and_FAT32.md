---
title: "BitTorrent and FAT32"
date: 2005-06-07
forum: General Help
---

### Post by foxy123 on 2005-06-07
I had this issue before and now again. For some reason I cannot download files using bittorrent on my fat32 partition. I tried to d/l into my /home and it worked fine. I tried amule to fat32 and it worked fine. BitTorrent worked fine only few days ago as well and since then nothing has been changed.

I used several BT clients with the same results. I've got something like:

```
Operation not permitted, setLength fails
``` 

The entry for my fat32 partition in fstab is below:

```
/dev/hda5       /windows/D      vfat    rw,users,gid=users,umask=0002,iocharset=utf8 0 0
``` 

Any help?

---

### Post by defkewl on 2005-06-07
What's the property of /windows/D ?
Perhaps the user doesn't have rw privileges.

---

### Post by foxy123 on 2005-06-07
[QUOTE=defkewl]What's the property of /windows/D ?
Perhaps the user doesn't have rw privileges.[/QUOTE]
The thing is that I can write to /windows/D without any problem, the error happens only with bittorrent...

---

### Post by kiddyfurby on 2005-06-07
did u try azureus? 
You will find "incremental file creation" , in options, files.
It says "required for FAT32 under linux"
go give it a try~!

---

### Post by stefanoaguiar on 2005-07-09
Hey there!

I had that same problem, and your tip got it fixed, kiddyfurby. Thx a lot!

---

### Post by Caboto on 2005-07-09
Thank you! Finally no startings/stopping torrents...
Seems like Azureus (or BT in general) can only write one file on a FAT32 Partition. Everytime you stop and start it again, it wrote another.

---

### Post by stefanoaguiar on 2005-07-23
[QUOTE=Caboto]Thank you! Finally no startings/stopping torrents...
Seems like Azureus (or BT in general) can only write one file on a FAT32 Partition. Everytime you stop and start it again, it wrote another.[/QUOTE]
 Caboto, didn't understand that. Does it mean I cannot restart my downloads on FAT32??

---

### Post by Mikebgr on 2006-04-30
thx kiddyfurby, solved my problem :)

---

