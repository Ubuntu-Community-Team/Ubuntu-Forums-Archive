---
title: "Need help configuring access permissions for Dropbox on Ubuntu properly,"
date: 2012-11-06
forum: General Help
---

### Post by s.v.z on 2012-11-06
Hi! I have a dual-boot PC with Win7 and Ubuntu 12.04 on board. I've just installed a Dropbox application on Ubuntu and set the folder path to /home/svz/data/Dropbox. 

Some explanation here: I have an NTFS drive mounted at /home/svz/data. The Dropbox folder is on that drive, cause I want it to be accessible from both Win7 and Ubuntu. 

The problem is that Dropbox application doesn't have permission to write to that folder (I think so). It managed to index all the files present there, but it cannot download new ones. 

The permissions for the folder are the following:
svz@svz-PC:~/data$ ls -l|grep Dropbox
drwxrwx--- 1 root plugdev  4096 Nov  6 23:37 Dropbox

I tried to do a chmod or a chown on that folder, but nothing changed. How can I solve this issue?

---

### Post by s.v.z on 2012-11-07
The only thing I could think of so far was to edit `fstab` and set UUID=000 for that partition. Works fine, though not a secure one..

---

### Post by dannyboy79 on 2012-11-07
here's a great guide about reading and writing to NTFS filesystems.

[http://opensuse.swerdna.org/susentfs.html](http://opensuse.swerdna.org/susentfs.html)

even though its SUSE linux it still applies.

---

