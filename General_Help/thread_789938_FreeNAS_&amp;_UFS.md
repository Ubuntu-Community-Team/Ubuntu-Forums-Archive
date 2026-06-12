---
title: "FreeNAS &amp; UFS"
date: 2008-05-11
forum: General Help
---

### Post by duren on 2008-05-11
Alright Gurus, I have a quick question.

I want to install FreeNAS in a VM to be my media gateway. I give it a local disk which it formats into UFS /w GPT.

If the machine explodes and I need to mount the disk in my ubuntu distro to retrieve files, I'll need to mount the UFS system (r/o is fine)..

I'm trying to accomplish this but hit a roadblock...

I'm using Ubuntu 8.04 and have UFS:

root@ubuntu:~# lsmod | grep ufs
ufs                    84996  0


my /proc/partitions shows /dev/sda but no partitions..

when I use sfdisk -l, I can see the GPT partition as
/dev/sdap1

but when I try to mount in read only mode

mount -r -t ufs -o ufstype=44bsd /dev/sdap1 /mnt/test

i get 

mount: special device /dev/sdap1 does not exist

I think because the system doesn't seem to see the partitions...

How can I fix this so I can mount that UFS system in Ubuntu?

---

