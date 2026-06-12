---
title: "External Hardrive"
date: 2007-04-28
forum: General Help
---

### Post by chiefbutz on 2007-04-28
I have an external hard drive, and it used to work just fine, and one time I think I accidentally changed where it mounted to automatically, and now it mounts to a different place and is read only, plus only root can access it. Can anyone help me to change where it mounts to? I am fairly new, but not so new that I have no clue what I am doing.

---

### Post by taurus on 2007-04-28
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by chiefbutz on 2007-04-28
Here you go:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.9G  4.3G  5.2G  46% /
varrun                506M  228K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  152K  506M   1% /proc/bus/usb
udev                  506M  152K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/disk/by-uuid/0CDC1696DC167A62
                       76G   64G   13G  85% /media/sda2
/dev/sdb1             150G   71G   79G  48% /media/usbdrive

```

The drive in question is /dev/sdb1. It normally mounts to /media/usbdisk

---

### Post by taurus on 2007-04-28
And I assume it's a ntfs.

```
sudo umount /dev/sdb1
sudo mount -t ntfs /dev/sdb1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```

---

### Post by chiefbutz on 2007-04-28
Well, that did it. I Changed /media/usbdrive to /media/usbdisk and it showed up so I could change the mount point for it. Thanks a lot. I don't know why i didn't think to try that.. I can use mount... oh well now I know for next time.

---

