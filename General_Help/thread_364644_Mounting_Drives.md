---
title: "Mounting Drives"
date: 2007-02-18
forum: General Help
---

### Post by lenwood on 2007-02-18
Hi All, I just installed a 6.06 LAMP server for personal use. I'm trying to get Webmin on the thing, and I can't for the life of me figure out how to get the file onto the server. My understanding is that I'm not to use apt-get for Webmin, so I loaded it to a USB flash drive, I can't mount it. So I burned it to a CD, and once again, I can't figure out how to mount. Since this is a server, I don't have any GUI. What commands do I use to mount USB flash drives and CDROMs?

Thanks,
Len

---

### Post by taurus on 2007-02-18
USB:
```
sudo mkdir /mnt/usb
sudo mout -t vfat /dev/sda1 /mnt/usb
ls -la /mnt/usb
```

CD-ROM:
```
sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc /mnt/cdrom
ls -la /mnt/cdrom
```

---

