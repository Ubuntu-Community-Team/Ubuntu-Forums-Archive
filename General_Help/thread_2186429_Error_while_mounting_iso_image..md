---
title: "Error while mounting iso image."
date: 2013-11-07
forum: General Help
---

### Post by AADAS on 2013-11-07
I have an iso image but I get wrong fs error.I am sure that the image is ok.

---

### Post by jamesisin on 2013-11-07
How are you trying to mount the ISO?

What is the exact text of the error you get?

How do you know the ISO is good?

---

### Post by AADAS on 2013-11-07
sudo mount -t iso9660 -o loop /bla/bla.iso /mnt/image/

mount: block device /bla/bla.iso is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by jamesisin on 2013-11-08
And how do you know the ISO is good?

---

