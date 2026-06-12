---
title: "Mounting Clonezilla images down't work?"
date: 2015-08-14
forum: General Help
---

### Post by gary64 on 2015-08-14
Hi,

I'm trying to mount ntfs disk images created with Clonezilla, but neither approach does work for me.

1) Using partclone: This command hangs the terminal window (no visible output, not even an error message):
```
sudo cat /media/sf_Desktop/sda1.ntfs-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.restore -C -s - -o /media/sf_Desktop/sda1.img

```
Further information: I'm running Vivid Vervet in a VirtualBox on a Mac host. The image files are on the host Desktop.  I had partclone installed using the Ubuntu Software Center.

1) Using ntfsclone: This command also hangs the terminal window (no visible output, not even an error message):
```
sudo cat /media/sf_Desktop/sda1.ntfs-ptcl-img.gz.* | sudo gzip -d -c | sudo ntfsclone --restore-image -o /media/sf_Desktop/sda1.img -

```
Any ideas?

Thanks a lot!

Gary

---

### Post by VMC on 2015-08-14
Use *zcat* instead of *cat*,  as the image is '.gz'

---

