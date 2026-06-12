---
title: "Software to synchronize folders"
date: 2006-07-26
forum: General Help
---

### Post by ammarr on 2006-07-26
Hello,

I have a usb drive I wish to keep synchronized with my documents on my HDD. I used to use fullsync/synctoy on windows. Are there any similar software available for linux? 

Regards..

---

### Post by Mau on 2006-07-26
I strongly recommend Unison -- a great program.  I use it for backing up to my usb drive.  It can also backup over FTP and SSH, I believe.

Two version available: CLI and GUI.  The CLI package is called "unison" and I think the GUI is "unison-gtk".  Check with synaptic.

---

### Post by wjp.reg on 2006-07-26
I'm with Mau - Unison works great.  Even available under the cygwin tool set to enable you to synchro between windows and linux.  Check out the Unison website for info [http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")
and [cygwin]("http://www.cygwin.com/")

cheers!

---

### Post by ammarr on 2006-07-26
Thanks a lot, it seems to be just what I want.

---

### Post by ammarr on 2006-07-28
Hello,

I'm having one little problem.. Permissions! It seems to think that all files are different because the files on my desktop and on the USB have different permissions. How do i tell it to check only file names/sizes/modification dates? Otherwise I have to look through the entire list just to see where the really changed files are.

---

### Post by guymauve on 2006-08-29
Would you detailed a little more...

Witch file system do you use un your usb Etc.

---

### Post by ammarr on 2006-08-31
Hello,

I managed to fix that by using -perms 0 (usb = fat32.. (its an sd card actually for my ppc) and desktop = ext3). Hopefully that'll help someone else :-)

---

### Post by rshel on 2006-09-10
Hi,

I also use UNISON to sync files on the hard drive to files on my sandisk 1gig usb flash drive and was recommending it to others as a great solution.  I had been having permissions problems but solved them after looking at various threads on how to reliably mount a usb flash drive (vfat) with read/write ability.  

HOWEVER, whenever I run a profile in UNISON to try to sync my hard drive files with the usb flash drive files, the flash drive becomes read-only. This occurs after UNISON has compared the two drives and determined the differences between them. So UNISON then refuses to write new files to the flash drive. The permissions of the flash drive still show rwx for user and group. This is not a consistent problem with my other usb drives. Any ideas?

---

### Post by rshel on 2006-09-10
Hi,

I also use UNISON to sync files on the hard drive to files on my sandisk 1gig usb flash drive and was recommending it to others as a great solution.  I had been having permissions problems but solved them after looking at various threads on how to reliably mount a usb flash drive (vfat) with read/write ability.  

HOWEVER, whenever I run a profile in UNISON to try to sync my hard drive files with the usb flash drive files, the flash drive becomes read-only. This occurs after UNISON has compared the two drives and determined the differences between them. So UNISON then refuses to write new files to the flash drive. The permissions of the flash drive still show rwx for user and group, but it will not let me write to it.  This is not a consistent problem with my other usb drives. Any ideas?

---

