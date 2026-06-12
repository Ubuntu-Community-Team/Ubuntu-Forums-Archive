---
title: "Not able to run a 755 exec"
date: 2007-02-14
forum: General Help
---

### Post by fouad167 on 2007-02-14
Hi,
I just can't understand what is wrong
I compiled subversion with --prefix=/root/usr/local 
I created a user apache adduser --system apache
ls -al svn gives
-rwxr-xr-x 1 root root 373803 Feb 11 13:49 svn
but  
sudo -u apache /root/usr/local/bin/svn
sudo: unable to execute /root/usr/local/bin/svn: Permission denied

Why can't user apache execute svn?
Thanks 

fmardini

---

