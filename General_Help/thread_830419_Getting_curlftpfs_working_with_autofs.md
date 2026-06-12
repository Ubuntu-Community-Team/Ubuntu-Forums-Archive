---
title: "Getting curlftpfs working with autofs?"
date: 2008-06-15
forum: General Help
---

### Post by shuhab on 2008-06-15
Hi, I have tried and tried but just can't make autofs work together with curlftpfs. I found a tutorial that showed how to get sshfs to work with it and tried to copy it and change some settings to match what curlftpfs would want, but it doesn't seem to work. I don't see any error messages from autofs anywhere, so don't really know where to go from here. 

I hope someone has tried this before and can help me out. 

my auto.master looks like this:

/mnt  /etc/auto.sshfs   uid=1000,gid=1000,--timeout=30,--ghost


my auto.sshfs looks like this:
fys  -fstype=fuse,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#username@host\:

servage   -fstype=fuse,rw,allow_other,user,uid=1000,gid=107,direct_io :curlftpfs\#host\:


The fys entry that is using sshfs is working perfectly, so I guessed that curlftpfs also should work but :(.


Shuhab.

---

### Post by VicAlpha on 2009-01-15
didn't tried it myself but it here's a solution 

[http://lukaszproszek.blogspot.com/2008/05/automounting-ftpfs-using-curlftpfs-and.html](http://lukaszproszek.blogspot.com/2008/05/automounting-ftpfs-using-curlftpfs-and.html)

---

