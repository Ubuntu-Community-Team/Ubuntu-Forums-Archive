---
title: "encfs and fuse"
date: 2007-12-11
forum: General Help
---

### Post by SagaciousKJB on 2007-12-11
```
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

```

I've been getting this error now after a first successful use of the program.  I recall that I did not unmount it correctly, and I'm wondering if that is the problem.  I've already done everything in this thread: [http://ubuntuforums.org/showthread.php?t=76693&page=2](http://ubuntuforums.org/showthread.php?t=76693&page=2) but it still won't work.

I should have permissions to run everything, but for some reason the only way I can make it work is to run it as root ( with sudo ), but then I can't even read the files under my normal user account, only with sudo.

---

### Post by maxino on 2007-12-24
Hi,

I got the same error as well.
I found out that after adding myself to the fuse group with

```
sudo adduser <my_username> fuse
```

the change would take effect only after rebooting the system - just log out and log in again just would not work.
After that everything was OK.

Hope it helps,

max(ino)

---

