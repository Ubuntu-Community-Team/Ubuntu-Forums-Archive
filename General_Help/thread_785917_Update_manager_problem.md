---
title: "Update manager problem"
date: 2008-05-07
forum: General Help
---

### Post by eberndl on 2008-05-07
I'm trying to complete an update that Ubuntu says I need (orange yield sign on task bar).  I open the update manager, and it says it has been 9 days since my last update.  I tell it to check for updates, and get this error message:
```
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

My Hardy Heron CD is in the computer, and is on my desktop (so I assume it's properly mounted).  Any idea of what I should do?

Thanks in advance.

---

### Post by juje on 2008-05-07
same problem here...i know the servers must be overloaded but its been three days without updating hardy heron...is it quite regular...do i have to keep on wating? just to know...its my first major upgrade!
thanxz

---

### Post by itaintover on 2008-05-07
have you tried it *Please use apt-cdrom to make this CD-ROM recognized by APT.* already?

[http://taufanlubis.wordpress.com/2008/02/11/using-apt-cdrom-when-update-ubuntu-through-dvd-repositories/](http://taufanlubis.wordpress.com/2008/02/11/using-apt-cdrom-when-update-ubuntu-through-dvd-repositories/)

---

### Post by eberndl on 2008-05-07
Yes I have, but I don't know which tag(s) to use... I've tried
```
sudo apt-cdrom
[sudo] password for lizz: 
apt 0.7.9ubuntu17 for i386 compiled on Apr 22 2008 15:20:01
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
```

and 
```
sudo apt-get update
SNIP
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
lizz@lizz-desktop:~$ 

```

---

