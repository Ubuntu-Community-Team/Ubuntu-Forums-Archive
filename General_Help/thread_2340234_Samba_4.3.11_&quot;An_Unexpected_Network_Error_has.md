---
title: "Samba 4.3.11 &quot;An Unexpected Network Error has occurred&quot;"
date: 2016-10-16
forum: General Help
---

### Post by ryan_3 on 2016-10-16
Hey All,


Okay so I am running a Glusterfs 3.7.16 with Samba-VFS-Modules installed. (ubuntu 14.04.3)
Previously was on Gluster 3.7.11 but upgraded over the weekend.
Now was on 4.1.6 of Samba and once Gluster was upgraded all my windows clients started receiving ""An Unexpected Network Error has occurred"" when trying to copy from or onto the samba share.


I upgraded Samba to 4.3.11-Ubuntu but am still receiving the same issues.
I wasn't first able to access the share points after the upgrade but after running 'apt-get install --reinstall libtevent0 libtalloc2’ I can now access it, just not copy from or onto.


Have increased logging on Samba but really the only consistent error I can find is - [http://paste.ubuntu.com/23336648/](http://paste.ubuntu.com/23336648/)
These are some more logs that just get repeated over and over
-> [http://paste.ubuntu.com/23336690/](http://paste.ubuntu.com/23336690/)


Does anyone have a similar issue with this version of Samba?
I mean even when I stop using samba-vfs-modules and just have a direct mountpoint I get the same issue.
log.smbd - [http://paste.ubuntu.com/23336705/](http://paste.ubuntu.com/23336705/)


Thanks,


Ryan

---

