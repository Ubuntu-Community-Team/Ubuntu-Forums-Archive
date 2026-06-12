---
title: "Access mounted sshfs folder using non-root user"
date: 2013-05-18
forum: General Help
---

### Post by bottlen3ck on 2013-05-18
I am trying to automatically mount a server folder through sshfs in my client /etc/fstab (sshfs#rtor@xxx.xxx.xxx.xxx:/home/rtor/IP   /home/ub/Desktop/SSHFS  fuse    _netdev,uid=1000        0       0).  The mount works for root when I 'sudo mount -a'.  However, I cannot access the drive through my main user (uid of 1000).  I own the folder I am trying to mount to on the client side, /home/ub/Desktop/SSHFS and have also tried chowning with, chown -R $USER /home/ub/Desktop/SSHFS (which freezes).  How do I access this mounted folder with my main user, not root.  Pls enlighten.  Thx

---

### Post by btindie on 2013-05-18
Take a look at the [FAQ]("http://sourceforge.net/apps/mediawiki/fuse/?title=SshfsFaq#Automatical_mounting_using_.2Fetc.2Ffstab") for SSHFS, that answers your question.

---

### Post by bottlen3ck on 2013-05-19
That FAQ direction worked.  Thanks

e.g. sshfs#guest@guest.login.com:data /mnt/guest fuse uid=1003,gid=100,umask=0,allow_other 0 0

---

### Post by superdaveozzborn on 2014-03-23
here is a quick tutorial on how to use sshfs. on step 2 shows you how to add your user to the "fuse" group which is needed for non root users to access the share.

[http://www.distrogeeks.com/mounting-remote-folders-with-ssh-ubuntu/](http://www.distrogeeks.com/mounting-remote-folders-with-ssh-ubuntu/)

this may help any one else having troubles using sshfs.

Thanks..

---

### Post by CaptainMark on 2014-03-23
I had an easier way round it when I had the same problem. Just scribbled a simple script for the sshfs mount command and added it the the users crontab, completely bipassed the fstab problem

---

### Post by superdaveozzborn on 2014-03-23
or you could setup an alias to do same thing with single command if you don't all ways want the folders mounted....

---

