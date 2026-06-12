---
title: "hard drive mounted in read-only"
date: 2006-09-05
forum: General Help
---

### Post by pwrstick on 2006-09-05
Ahoy hoy,

I have a USB2.0 external hard drive mounted successfully, but am unable to write to it without root privs.  I.e. 'touch bleh' doesn't work, while 'sudo touch bleh' does.

This is not desirable as it's meant to be a general storage drive.  Any ideas on what I can do to circumvent this?

Here's its fstab entry:
/dev/sda        /mnt/external   ext3    defaults        0       0

And a mount output for the drive:
/dev/sda on /mnt/external type ext3 (rw)


And it's been initialized as an ext3 drive.

Cheers

---

### Post by pwrstick on 2006-09-05
A der?!  I just ran fdisk -l to maybe get some more information and got the following!


```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table
```

I didn't even think to check for this because there is a directory named "lost+found" and I can write files via sudo.  So now I'm more confused.

Should I be using parted to fix this?  (this is a server install so it's command line only).

---

