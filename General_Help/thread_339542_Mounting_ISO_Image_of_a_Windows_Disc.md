---
title: "Mounting ISO Image of a Windows Disc"
date: 2007-01-15
forum: General Help
---

### Post by tnunamak on 2007-01-15
I have an iso image of program for windows. I tried mounting it with 
```
sudo mount -o loop -t iso9660 image.iso /mnt/iso
```

But I got the following errors:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I'm guessing this is because the iso file uses an NTFS filesystem? Is there a way I can mount it? I use ntfs-3g to mount my windows hard drive, would it be able to manage iso files?

Thanks

---

### Post by bodhi.zazen on 2007-01-15
make sure your mount point exists first:

```
sudo mkdir /mnt/iso
sudo mount -o loop -t iso9660 image.iso /mnt/iso
```

And, of course, use the name/path to the iso

HTH

---

### Post by meng on 2007-01-15
The error message suggests to me that the ISO is bad. ISO does not use NTFS, it's essentially a different filesystem altogether.

---

### Post by tnunamak on 2007-01-16
I think you're right about having a bad ISO. Thanks.

---

