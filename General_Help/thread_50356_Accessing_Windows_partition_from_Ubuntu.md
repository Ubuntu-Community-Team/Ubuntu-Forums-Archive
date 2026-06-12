---
title: "Accessing Windows partition from Ubuntu"
date: 2005-07-20
forum: General Help
---

### Post by diffuser78 on 2005-07-20
Hello,

I have a dual boot machine with Windows XP and Ubuntu on it. 

Could somebody tell me how can I access files from Windows partition while I am on Ubuntu. I am sure there must be some way of doing it.

Please help guys,

Thanks,

Dan

---

### Post by uniko on 2005-07-20
[Ubuntuguide](http://www.ubuntuguide.org/#mountunmountntfs)  has pretty decent instructions. Lots more useful information on there, too.

---

### Post by diffuser78 on 2005-07-20
[QUOTE=uniko][Ubuntuguide](http://www.ubuntuguide.org/#mountunmountntfs)  has pretty decent instructions. Lots more useful information on there, too.[/QUOTE]

I checked that out ..but running that i get the following error

I did 

sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

and got the following

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any other options please,

Dan

---

### Post by Adrenal on 2005-07-20
[QUOTE=diffuser78]I checked that out ..but running that i get the following error

I did 

sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

and got the following

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any other options please,

Dan[/QUOTE]
 Is it formatted to ntfs or fat?
And have you made the folder /media/windows

---

### Post by diffuser78 on 2005-07-20
[QUOTE=Adrenal]Is it formatted to ntfs or fat?
And have you made the folder /media/windows[/QUOTE]

Formatted to ntfs and yes i did creat /media/windows

Thanks for your help...please suggest more options

dan

---

### Post by uniko on 2005-07-20
As it is ntfs you must use -t ntfs, not -t vfat. Try:

mount -t ntfs -o umask=0222 /dev/hda1 /media/windows/

Tell if this works. If not, post what sudo fdisk -l tells you.

---

### Post by diffuser78 on 2005-07-20
[QUOTE=uniko]As it is ntfs you must use -t ntfs, not -t vfat. Try:

mount -t ntfs -o umask=0222 /dev/hda1 /media/windows/

Tell if this works. If not, post what sudo fdisk -l tells you.[/QUOTE]


Thanks, it worked!!!!

---

