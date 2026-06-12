---
title: "delete key not working on mounted windows partition but I am able to delete"
date: 2015-09-29
forum: General Help
---

### Post by gaytripperg on 2015-09-29
I have the following problem. In mounted windows partition the DEL key seems not work. I able to delete file by right clicking on files and selecting the delete option.
The strange thing is that the del key works perfectly on the linux partition. I am on a dell laptop latitude e5450 (italian keyboard layout).
 I am on ubuntu 15.04. I mount the windows partition as OS automatically by the fstab, 
This is my fstab:
UUID=myuidnumber  /media/windir  ntfs-3g  defaults,umask=000,windows_names,locale=en_US.utf8  0 0

Thank you in advance for any help!

Joe

---

### Post by bapoumba on 2015-09-29
Thread moved out of the Resolution Centre to General Help.

---

### Post by gaytripperg on 2015-10-08
update: 
if I do not use fstab to mount windows partition, the partition is mounted only after I clicked on OS icon on files explorer. In this case the partition is mountend under /media/myname/OS. After that I am able to delete files by clicking on the Del key of the keyboard. The problem is that I cannot run dropbox, linked to a directory of the win partition, before to manually clicking on the OS icon of the file explore. Ohterwise, if I mount the partition through fstab, it is impossible to delete files through del key (but strangely it is possible to do by right clicking the file and selecting delete). Is it a bug? 
Thanks,
Joe

---

