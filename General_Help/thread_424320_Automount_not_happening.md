---
title: "Automount not happening"
date: 2007-04-26
forum: General Help
---

### Post by ben.christey on 2007-04-26
I have added a mount point in my /etc/fstab to mount my samba fs. If i type "mount -a" then it mounts fine however on rebooting it does not automatically mount. 

So what have i done wrong then? My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e105870d-c0e5-43e4-8657-f972d86d26ef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=40ab8319-a131-42f2-98f4-97f7e3782af1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
//ben_desktop/bigshare /home/ben/bigshare smbfs defaults 0 0


any ideas on this one?

---

### Post by DugieHowsa on 2007-06-27
You should try using cifs.  This post states that smbfs is unstable and no longer under active development:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

The following is also a very good post on how to configure cifs and gives a few examples on how to automatically mount cifs shares at boot.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

