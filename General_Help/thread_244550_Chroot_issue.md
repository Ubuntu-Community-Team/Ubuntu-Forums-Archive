---
title: "Chroot issue"
date: 2006-08-26
forum: General Help
---

### Post by SigmaX on 2006-08-26
I have a spare partition on my Dapper laptop, and was trying to install Gentoo on it from Ubuntu.  I downloaded my Stage3 and Portage tarballs and extracted them onto /mnt/extra, and proceeded to 'chroot' into /mnt/extra.

I ran 'env-update' once there.  This action apparently had severe repercussions, and I promise I won't do it again!  My first problem was when I tried to run 'source /etc/profile', and it spit back some errors.

Now, after reboot and everything, when I attempt to chroot I get:

```
/bin/bash: reolocation error: /lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
```

Help?!

SigmaX

---

### Post by DeShark on 2006-08-26
If it were me, I'd probably try the whole process again. Start from scratch, making sure that I untar-ed the tar files with permissions and making sure that portage was placed in /usr. I'd also make sure that the files were correct by checking the MD5 or whatever on them... just to be doubly sure. There may be a better way, but since you aren't far through the handbook, starting again might be better, just remove everything, re-download the tarred files and re-extract them.. It's the best advice I can give I'm afraid.

---

