---
title: "Trouble making an iso image using dd"
date: 2007-12-19
forum: General Help
---

### Post by kratos777 on 2007-12-19
I was wondering if anyone could help me use dd. I was following a websites instructions on creating an iso image of a cd, but it is not working. I don't think I am using the right location for the cd. Any help is appreciated.

---

### Post by solar george on 2007-12-19
Could you post the command you tried.

---

### Post by kratos777 on 2007-12-19
[COLOR="DeepSkyBlue"]Do not mount CD. Verify if cd is mounted or not with mount command:

# mount

If cd was mouted automatically unmout it with umount command:

# umount /dev/cdrom

OR

# umount /mnt/cdrom

Create CD-ROM ISO image with dd command:

# dd if=/dev/cdrom of=/tmp/cdimg1.iso[/COLOR]

These are the instructions I followed, it would start copying then stop at 1.7Mb

---

### Post by solar george on 2007-12-19
If the cd appears on your desktop type,
```
mount
```

Look for the line that mentions /media/cdrom* and post it back.

---

### Post by kratos777 on 2007-12-19
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=acordova)

---

### Post by solar george on 2007-12-20
/dev/scd0 is the location for your cdrom.

Try,
```
sudo -s
umount /dev/scd0
dd if=/dev/scd0 of=/home/username/cdimage.iso
chown username:username /home/username/cdimage.iso
```

Replacing username with your username.

---

