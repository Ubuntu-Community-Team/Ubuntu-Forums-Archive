---
title: "Mounting a second hard drive to multiple points"
date: 2006-12-29
forum: General Help
---

### Post by scratched on 2006-12-29
I just finished installing unbuntu server on an old machine I have. Unfortunately, the BIOS is so old I couldn't install the main OS on the primary 200GB drive because of compatibility issues at boot.

I instead installed the OS on a smaller hard drive and I want to try mounting the larger hard drive to specific points on the system, /home, /var/www, etc...

Is there any way to mount a single partition to multiple points on the file system?

Or maybe another way to partition my drives so that just information need to boot is installed on the smaller drive and the rest of the FS is installed on the main drive....

---

### Post by scratched on 2006-12-29
I managed to solve my issue by re-formatting and assigning the smaller HD as the /boot partition, using the large hard drive as /, and making sure GRUB installs to the smaller /boot partition.

---

