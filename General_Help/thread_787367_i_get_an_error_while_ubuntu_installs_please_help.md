---
title: "i get an error while ubuntu installs please help"
date: 2008-05-08
forum: General Help
---

### Post by snes1 on 2008-05-08
k i used wubi to install ubuntu, and the dual boot works and when ubuntu loads and unzips all the files i get this error


Loop-mounted file systems already present
The selected partition (partition 1 of /var/lib/partman/devices/=dev=sdb) already contains the following file system images:

/ubuntu/disks/root.disk

Please uninstall these before trying again.
[OK]

---

### Post by garyedwardjohnston on 2008-05-08
Delete the entire directory then try installing again.

---

### Post by snes1 on 2008-05-09
dang are u serious haha

ehh, is it because i downloaded it to the e drive?

---

### Post by ago on 2008-05-09
This is probably because  of an interrupted previous installation. Wubi for obvious reasons, will refuse to install on top of a pre-existing installation. You have to remove that first.

---

### Post by snes1 on 2008-05-09
okay im going to download ubuntu off the site, but where do i put the file? after i dl it

because now when i try and download it i get an error msg

---

### Post by snes1 on 2008-05-09
okay i deleted it and tryed to just copy and paste the iso file but i downloaded the wrong one so i just deleted it and then i tryed to download using wubi again, and now i get a blank error again
the top part is what was gion on i guess it failed trying to rename it... but i deleted it many times and tryed many verisons of wubi




renameE:\ubuntu\install\MD5SUMS-metalink.gpg->E:\ubuntu\install\MD5SMUMS-metalink.asc

the download was interrupted with the error:

---

### Post by ago on 2008-05-09
Uninstall wubi, then delete c:\ubuntu and c:\ubuntu-backup (if any)
Then run wubi again and let it download the ISO for you.
Once you are there you might want to run chkdsk /r on the target drive

---

### Post by snes1 on 2008-05-09
whats check disk? and when and how do i do it?

---

### Post by snes1 on 2008-05-09
here is the error i get when i try and reinstall wubi

[http://i32.tinypic.com/2i8ulb8.jpg](http://i32.tinypic.com/2i8ulb8.jpg)

---

