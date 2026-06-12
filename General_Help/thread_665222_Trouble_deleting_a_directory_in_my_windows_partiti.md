---
title: "Trouble deleting a directory in my windows partition from Ubuntu"
date: 2008-01-12
forum: General Help
---

### Post by sethosayher on 2008-01-12
Okay, so I decided to transfer a directory of about 24 gigs from my windows vista partition to my external HDD in Ubuntu, as I've experienced sluggishness in transferring files when in Vista.  After several hours, the transfer is complete and I moved the original directory to the trash (still in ubuntu) by right clicking and selecting the appropriate option. When I went to the trash nothing was there. Looking at the disk statistics the same amount of data is being taken up, so apparently the directory is still there. Boot up in vista, I can't find the directory, and when I search for it I get tons of results but upon clicking the results I'm told that the files can't be located. 

Any ideas?

---

### Post by shadyedsan on 2008-01-12
the reason your probably seeing the files but not being abe to use them is maybe to do with the filing systems. windows can't read any other files on other filing systems apart from FAT (and variants) and NTFS but might be able to see them. what is the filing system type you are using i.e. NTFS or reiferfs, ext2 etc? the reason i ask is that ubuntu can gain access to other filing systems if the correct plugins or decoders are installed but windows can't. what is the formatted filing system you are using on the external HDD?

are the files usable in ubuntu?

---

### Post by mojoman on 2008-01-12
Check your fstab. Is the windows disk mounted as read-only? If so, there you have it.
/mojoman

---

### Post by kr152ta on 2008-01-12
If there is an NTFS patition the ntfs-3g packages must be installed to get write access on ntfs patitons. 
In fstab you must see something like that:
UUID=3CC826EEC826A5DC /media/sdb2     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1

After the mount point goes the file system type. That is by default ntfs, and must be altered to ntfs-3g.

Hope it helps.

---

### Post by danwood76 on 2008-01-12
ubuntu has problems deleting stuff from NTFS partitions in the sence that it moves them to the trash folder on that drive but the trash folder isnt linked to the gnome menu.

go to the root of the drive and press ctrl-h to display the hidden folders and look for a .Trash-username and see if the files are in there, if they are select them all and right click and click delete and they will actuallly delete.

regards,
Danny

---

### Post by sethosayher on 2008-01-12
Thanks Dan, your solution worked. I'm now 24 gigs slimmer =D

Thanks to the rest of the posters for your thoughts and advice.

---

### Post by danwood76 on 2008-01-12
No problem, Im glad to help.
Hopefully this bug is worked out in the next release of ubuntu now that the ntfs-3g driver is included as default.

regards,
Danny

---

### Post by Kingsfan on 2008-01-20
awesome, worked for me too, thx!

---

