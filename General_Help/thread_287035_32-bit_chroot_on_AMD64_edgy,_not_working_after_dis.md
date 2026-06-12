---
title: "32-bit chroot on AMD64 edgy, not working after dist-upgrade"
date: 2006-10-28
forum: General Help
---

### Post by Iesos on 2006-10-28
Hi. I have been using chroot on my amd64-ubuntu the last two versions (breezy and dapper). Now when I updated to edgy it stoped working. This is what happened:
I ran:
```
$ dchroot -d
```
to enter my chroot enviornment, and it gave me the following message:
```
E: locale::facet::_S_create_c_locale name not valid
```
I thought this just was something that went wrong during the upgrade, so I tried to reinstall chroot ([http://www.ubuntuforums.org/showthread.php?t=24575)](http://www.ubuntuforums.org/showthread.php?t=24575)), the same way as I installed it on my breezy. But the during the
```
$ sudo debootstrap --arch i386 hoary /chroot/ http://archive.ubuntu.com/ubuntu
```
step I got some error about monting /proc (what was that all about?). I started reading on the ubuntu-wiki and other places on the forum which lead me to realize that maybe removing my current chroot and making a new one would work.
But something was wrong with /chroot, I had to use /var/chroot. Now, I just completed the installation. Everything went fine, but when trying to enter my chroot enviornment I got the same message again:
```
E: locale::facet::_S_create_c_locale name not valid
```
Can anyone help me with this?

---

### Post by rsidd on 2006-10-31
I had the same problem.  I fixed it with "export LANG=C".

It appears that many ubuntu programs, like dchroot, don't like the configured locale.  Most of them just default to "LANG=C" but dchroot doesn't.

---

