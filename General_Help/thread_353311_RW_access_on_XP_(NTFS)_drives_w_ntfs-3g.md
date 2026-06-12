---
title: "RW access on XP (NTFS) drives w ntfs-3g"
date: 2007-02-04
forum: General Help
---

### Post by kenerly on 2007-02-04
I posted this over at kubuntu and have yet to get a reply, so hope you all can help.


I'm trying to at least have read access to my ntfs partitions,  write would be nice also, or at least copy from and to.

I install ntfs-3g and fuse using Adept. I made mount points (folders I guess - xp user here). When I click on the folder say C it opens with no content. I can right click it and mount, same result.

Here is my fstab.
> proc /proc proc defaults 0 0
# Entry for /dev/hdc3 :
UUID=054d6b62-bfad-4b51-9ef8-ef0a2e77cc30 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/hdc4 :
UUID=0a71a42c-8a58-41d9-9294-7cab78af1998 none swap sw 0 0
/dev/hdd /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 /media/C ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/hdc1 /media/E ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/hdb5 /media/F ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/hdc5 /media/I ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/sdb5 /media/J ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/sdb1 /media/K ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0
/dev/sdb6 /media/L ntfs-3g defaults,locale=en_US.nls=utf8,umask=0222 0 0

Here is a pic of the drives.
[img]http://christiangamers.net/images/media.jpg[/img]


Thanks for any help.

---

### Post by taurus on 2007-02-04
Try to remove the **umask=0222** thing in /etc/fstab.  Then, reboot.

---

### Post by kenerly on 2007-02-04
> **taurus said:**
> Try to remove the **umask=0222** thing in /etc/fstab.  Then, reboot.

That is how I had it before adding the unmask=0222, same result with it removed.

---

### Post by taurus on 2007-02-04
Here is what it should look like.

```

/dev/hda1     /media/C     ntfs-3g     defaults,locale=en_US.utf8   0    0

```

---

### Post by kenerly on 2007-02-04
I tired it like that taurus before I added the unmask, same result.

---

### Post by taurus on 2007-02-04
And you sure you've installed ntfs-3g, right!

---

