---
title: "Permissions with VSFTPD on external mounted NTFS drive"
date: 2014-09-06
forum: General Help
---

### Post by sean59 on 2014-09-06
Hi there.  I have managned to mount my NTFS drive with FSTAB and set up an ftp account chrooted to an FTP folder.  I would like to be able to set restrictions on this account though so they can't write in the actual ftp folder but they can write to the uploads folder.  

I know I can't use the traditional Chmod on this seeing as its NTFS.  Is there anyway around this.

Thank You

---

### Post by TheFu on 2014-09-07
Use a Linux file system?
or control the mount options (owner/group/permissions) for the NTFS partition. Lots of how-tos for this exist.

Oh - and I'd be remiss for not asking you to [Stop using FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").

---

### Post by nerdtron on 2014-09-07
Another workaround on this problem is to have the folders with permission on you local Linux file system. Then write a script that runs on an interval that will move the files to their designated location on the NTFS drive.

---

