---
title: "Why can't I perform chroot to mandriva???"
date: 2006-11-10
forum: General Help
---

### Post by nadavvin on 2006-11-10
Hello

I want to perform chroot to mandriva from ubuntu to check the wine version for this topic:
[http://mandrivausers.org/index.php?showtopic=36804](http://mandrivausers.org/index.php?showtopic=36804)

But I get permission denied while I'm in root:
```

$ sudo su
root@nadav-desktop:/# chroot /media/hda
hda1/ hda5/ hda7/
root@nadav-desktop:/# chroot /media/hda5
chroot: cannot run command `/bin/bash': Permission denied
root@nadav-desktop:/# ls /media/hda5/bin/bas
basename  bash	  bash3

```

What is the problem?

How It's possibility to block the **root**?
[http://mandrivausers.org/index.php?showtopic=36838](http://mandrivausers.org/index.php?showtopic=36838)

---

### Post by lloyd_b on 2006-11-10
Could you run this:

```
**ls -l /media/hda5/bin/bash**
```

Note, if the execute bit isn't set, then even root will get a "permission denied" message. 

Lloyd B.

---

### Post by nadavvin on 2006-11-10
```

$ ls -l /media/hda5/bin/bash
-rwxr-xr-x 1 root root 725160 2006-08-24 18:05 /media/hda5/bin/bash

```

I can perform chroot to LFS
```

$ ls -l /media/hda7/bin/bash
-rwxr-xr-x 1 root root 1440852 2006-09-14 16:32 /media/hda7/bin/bash

```

---

### Post by lloyd_b on 2006-11-10
Well, it was a thought....

Have you tried running any other commands via the "chroot"?

```
**sudo chroot /media/hda5 /bin/ls**
```

and see if you get the same results.  I'm curious if the issue is just with "bash", or if it's every executable....

Lloyd B.

---

### Post by nadavvin on 2006-11-10
```

/$ sudo chroot /media/hda5 /bin/ls
Password:
chroot: cannot run command `/bin/ls': Permission denied

```

---

### Post by boban on 2006-11-10
how did you mount that partition?
If it was  mounted during boot, then post your fstab file... 

(I presume that you have mounted that partition with "noexec")

---

### Post by nadavvin on 2006-11-10
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda8 -- converted during upgrade to edgy
UUID=92bb4267-8290-40f6-b016-d515d8986c1d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=EE8CA9BF8CA98327 /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda5 -- converted during upgrade to edgy
# /dev/hda7 -- converted during upgrade to edgy
UUID=0bd160de-3e09-4132-8395-3b7b36d9580e /media/hda7 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda6 -- converted during upgrade to edgy
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda5 /media/hda5 ext3 nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/hda7 <mount\040point> swap auto 0 0

```

It is with noexec.

But how hda7 is mount as swap?

It's the LFS partition which I have access to its files and I can perfor, chroot.

and it mount in the boot.

---

### Post by nadavvin on 2006-11-10
It's work!!!

I remove the noexec and now I can perform chroot.


How do you explain the hda7 partition?

---

### Post by boban on 2006-11-10
> **nadavvin said:**
> It's work!!!

I remove the noexec and now I can perform chroot.


How do you explain the hda7 partition?

Hmm... I think it's all about noexec.... From the man:

> 
**noexec** Do not allow direct execution of any binaries on the mounted file system. 


Your LFS partiton dosn't have noexec so you can do what you wan't... And you have something messed up in fstab... see:

> 
UUID=0bd160de-3e09-4132-8395-3b7b36d9580e /media/hda7 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

/dev/hda7 <mount\040point> swap auto 0 0


If UUID=0bd160de-3e09-4132-8395-3b7b36d9580e is mounted as /media/had7, then I assume that it is /dev/hda7 (but it don't have to be). And then you have /dev/hda7 mounted again as swap?  (I don't know if <mount\040point> means something...)

Conclusions:
- either your partition mounted to /media/hda7 isn't /dev/hda7 (check with gparte or fdisk /dev/hda, then p, then q)
- or second time you try to mount /dev/hda7 isn't mounted at all

But if I were you, I would rewrite fstab from scratch...

---

