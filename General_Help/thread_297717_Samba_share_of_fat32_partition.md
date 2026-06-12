---
title: "Samba share of fat32 partition?"
date: 2006-11-11
forum: General Help
---

### Post by ArgentSilver on 2006-11-11
I have a dual boot system which has a fat32 partition on it. When booted into Dapper, I want to share a folder on that partition with the rest of my home network. But here's the problem: I need that folder and the files in it to have read/write access from other Windows PCs on the network. I've managed to get read access OK, but no write access. And no amount of rummaging around in the smb.conf or permissions has helped. Anyone know how to do this?

---

### Post by zek725 on 2006-11-11
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

---

### Post by ArgentSilver on 2006-11-12
> **zek725 said:**
> [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

Yeah, I'd already been through that. A good guide, but my specific question doesn't seem to be covered.

I have a little more info now: I think(!) that the problem is that the Linux system is assigning ownership of the Fat32 Windows partition to root. I have an entry in fstab so that partition gets automounted during boot. Presumably this is a pseudo-ownership of convenience, since files on a Win partition don't have that characteristic? Anyway, I can't edit or delete those files without the use of sudo, and the system won't let me chown them (even with sudo). I believe that's why there's no write access via Samba.

I don't know enough Linux yet to fix it. Is there something in the fstab config?

EDIT: Yep, there is. Turns out the 'defaults' option in fstab mounts it read/write...for root only! Changing that to 'umask=0000' resolved the issue. Thanks to Google & the Gentoo Wiki for helping. Wish I could say it was this forum, but maybe this may help somebody else.

---

### Post by nemolomen on 2008-06-18
> **ArgentSilver said:**
> 
Wish I could say it was this forum, but maybe this may help somebody else.

You just did, thanks.

---

