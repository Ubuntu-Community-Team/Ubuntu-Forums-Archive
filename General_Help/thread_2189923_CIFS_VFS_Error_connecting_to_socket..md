---
title: "CIFS VFS: Error connecting to socket."
date: 2013-11-24
forum: General Help
---

### Post by rwb1959 on 2013-11-24
I saw a "solved" thread with this topic but it did not help me so please forgive me for starting a new thread.
I am running ubuntu 13.10 and I update regularly (checking daily). I recently (about 10 days ago) installed cifs to mount shares on a network storage device (the shares are presented as windows share to the network). All worked fine until 2 days ago. Ultimately, the shares do mount and are usable however, I get the following error (repeated several times) on boot:

kern.log.1:Nov 22 14:49:24 mike-ws1 kernel: [   24.773404] CIFS VFS: Error connecting to socket. Aborting operation.
kern.log.1:Nov 22 14:49:24 mike-ws1 kernel: [   24.774041] CIFS VFS: cifs_mount failed w/return code = -101

My fstab has not changed since I made the following additions 10 days ago. They are:

//10.1.10.210/public	/media/windowsshare/public	cifs	uid=mike,credentials=/home/mike/.smbcredentials,iocharset=utf8,sec=ntlm	0	0
//10.1.10.210/data	/media/windowsshare/data	cifs	uid=mike,credentials=/home/mike/.smbcredentials,iocharset=utf8,sec=ntlm	0	0

Although all seems to work fine, I am hoping to find out the root cause for the error. Any information would be greatly appreciated.

Thanks

---

