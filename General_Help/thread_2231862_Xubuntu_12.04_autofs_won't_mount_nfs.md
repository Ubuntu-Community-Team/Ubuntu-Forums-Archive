---
title: "Xubuntu 12.04 autofs won't mount nfs"
date: 2014-06-28
forum: General Help
---

### Post by jackson6 on 2014-06-28
Hello,

i would like to mount a nfs share from my server with autofs but i have some troubles with it.

What i did so far:

- apt-get install autofs
- in /etc/auto.master i added the line /home /etc/auto.home
- /etc/auto.home i added  * -fstype=nfs 10.0.0.2:/home/&
- with chmod 644 auto.home i set the right user rights
- after a service restart i get in syslogs: umount_autofs_indirect: ask umount returned busy /home

What am i doing wrong?

---

### Post by steeldriver on 2014-06-28
Hello and welcome to the forums

Is something else getting mounted on /home before the automount attempts to mount there ? What is the output of 'mount | grep home'?

---

