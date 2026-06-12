---
title: "NFS Export of AUFS mount?"
date: 2008-06-02
forum: General Help
---

### Post by idomagic on 2008-06-02
Hello

I'm having some trouble with exporting an AUFS mount (which should be NFS-exportable, no?), on the server I always get ```
exportfs: Warning: /media/ufs does not support NFS export.
```
And if I try to mount that export on the client I simply get ```
mount.nfs: 192.168.1.4:/media/ufs failed, reason given by server: Permission denied
```

It's mounted (and working properly locally) on the server with the following in /etc/fstab:```

none           /media/ufs      aufs    dirs=/media/hda1:/media/hdb1:/media/hdd1:/media/hde1:/media/hdf1:/media/hdg1:/media/hdh1:/media/hdi1:/media/hdj1:/media/hdk1:/media/hdm1:/media/hdn1    0    0
```

In /etc/exports I have:```
/media/ufs 192.168.1.6(root_squash,fsid=2000)
```
(and no other exports with fsid=2000)

If I use showmount -e 192.168.1.4 (server ip), the export /media/ufs shows up along with my client IP. Neither /var/log/syslog nor dmesg shows anything that seems interesting, /var/log/daemon.log does however show this:```
Jun  2 15:32:03 192.168.1.4 mountd[8461]: authenticated mount request from 192.168.1.6:858 for /media/ufs (/media/ufs)
```

Exporting any other mount works without a hitch.

On my server I'm using 
Xubuntu 8.04
Linux idoserver 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux
aufs-tools 0+20080129-1 (from ubuntu repository)

Anyone know what I'm doing wrong?

---

### Post by kenkarniff on 2008-06-30
Hi!

You have to compile the module with CONFIG_AUFS_EXPORT defined.. unfortunatelly the ubuntu-supplied version doesn't have that option...


K

---

