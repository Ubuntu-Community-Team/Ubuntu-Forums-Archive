---
title: "Image internal hard drive to file on external media."
date: 2012-11-12
forum: General Help
---

### Post by kio_http on 2012-11-12
Hi, I want to image the entire contents of my Hard-drive to a file on external media.

The resulting file should be mountable on both Windows and Linux. (At least the NTFS partition).

Which is a better idea?

dd sda1, sda2, sda3 ...

or

dd sda

Also how should I mount the resulting file/s? I have ext4 and ntfs partitions. If it is possible instead of dd, a method of delta copying like rsync does would be nice. I presume the backup would need to be done from a live usb.

---

