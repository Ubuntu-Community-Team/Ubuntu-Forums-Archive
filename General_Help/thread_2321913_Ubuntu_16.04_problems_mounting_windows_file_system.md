---
title: "Ubuntu 16.04 problems mounting windows file system in fstab"
date: 2016-04-25
forum: General Help
---

### Post by Mahyar on 2016-04-25
Since upgrading to 16.04, my /etc/fstab isn't automounting a Windows share upon boot, so I've written a script that gets called by /etc/rc.local. It's a simple "mount -a".

But then *that* doesn't get called when the PC wakes up from suspend.

The relevant /etc/fstab entry is:

//192.168.1.10/server	/home/Server	cifs	guest,uid=1000,iocharset=utf8	0	0

As stated, "mount -a" gets it up when fstab and rc.local don't.

If anyone can help, please do.

---

### Post by CharlesA on 2016-04-25
Move to own thread. Original thread can be found here:
[http://ubuntuforums.org/showthread.php?t=2321847](http://ubuntuforums.org/showthread.php?t=2321847)

---

### Post by alimo2 on 2016-12-09
I have same problem! I must `mount -a`  every time after login!

my fstab:

//192.168.10.1/test  /media/my_dir cifs credentials=/home/test/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0644,dir_mode=0755 0 0

---

### Post by wildmanne39 on 2016-12-09
Hello, you should start your own thread because this one his old and never had a reply to help, plus the OP never returned.
Thanks

---

