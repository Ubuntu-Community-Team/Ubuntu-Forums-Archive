---
title: "How to copy files from Live USB with persistence"
date: 2014-08-19
forum: General Help
---

### Post by jj.wauters on 2014-08-19
How can I copy files saved on my Live USB to my harddisk?

When booting from Live USB I have no writing rights on the harddisk.
When booting from harddisk I do not find a home map on the Live USB and I don't find my saved files in the Casper map.

---

### Post by marco-parillo on 2014-08-19
> **jj.wauters said:**
> How can I copy files saved on my Live USB to my harddisk?

When booting from Live USB I have no writing rights on the harddisk.
When booting from harddisk I do not find a home map on the Live USB and I don't find my saved files in the Casper map.
Once your hard disk is mounted, you should be able to write to it from a live USB.
I know I can: [http://ubuntuforums.org/showthread.php?t=2239171&page=2&p=13099908#post13099908](http://ubuntuforums.org/showthread.php?t=2239171&page=2&p=13099908#post13099908)
It might be difficult to mount if it is encrypted.

---

### Post by sudodus on 2014-08-19
It should be possible to loop mount your casper-rw file. Try the following command (when booted from the hard disk drive)

```
sudo mount -o loop /path-to-the-usb-drive-when-mounted/casper-rw /mnt
```

and you should see the directory and files at **/mnt**

---

### Post by jj.wauters on 2014-08-20
This worked fine. Thanks fot your help.

---

### Post by sudodus on 2014-08-20
You are welcome :-)

---

