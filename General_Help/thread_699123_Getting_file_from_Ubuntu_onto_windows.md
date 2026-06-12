---
title: "Getting file from Ubuntu onto windows"
date: 2008-02-17
forum: General Help
---

### Post by P-51 Mustang on 2008-02-17
Hello, I am new to Ubuntu; I have just installed Ubuntu 7.10 and made it very pretty with compiz :-).  But I have a 4 gig file on Ubuntu I need to get onto my Windows XP machine and i'm not sure how to do this.  It is two differant computers on the same network.  I dont want to pull out the HD's and i cant email the file to myself or put it on a cd or flash drive.  Does anyone know how I can move the file over my network?  Thanks!!!

---

### Post by &amp;)ky#)^ on 2008-02-17
You have a few options.  You could set up an ftp share on your ubuntu box or you could set up an ftp share on the windows box.  Either way, you can use an ftp client on one of the computers to move it.  Or you can set up a samba share on one of the computers and connect that way, but in my experience samba is a pain to set up.

Here's a helpful article about Samba in Ubuntu:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

This article explains the easiest way I can think of to use sftp to do the job:
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

Good luck.  It's not as bad as it looks.

---

### Post by legzelda on 2008-02-17
You could also access your Linux partition from Windows, assuming you're using the ext2 or ext3 filesystem format.  Check out [http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/](http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/) for a nice tutorial.

---

