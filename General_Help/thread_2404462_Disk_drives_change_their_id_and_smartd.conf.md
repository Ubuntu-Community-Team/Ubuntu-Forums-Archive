---
title: "Disk drives change their id and smartd.conf"
date: 2018-10-24
forum: General Help
---

### Post by David_Partridge on 2018-10-24
I have a SATA disk which I boot from, and a RAID array behind an Adaptec RAID controller

Most times when I boot the system the SATA device is /dev/sdb and the RAID array is /dev/sda but just a few minutes back I issued a "reboot" command and the system came up with the SATA as /dev/sda and the RAID as /dev/sdb

This rather makes it hard to configure the smartd.conf file correctly!!!

How can make sure the devices come in with constitent IDs?

Thanks
Dave

---

### Post by David_Partridge on 2018-10-24
The reboot brought in an updated kernel which appears to have swapped the devices round - I'll keep an eye on this.

Dave

---

### Post by dino99 on 2018-10-24
hm, what that means ? a random array lost ?
Glance at journalctl about that , it might help you understand the problem.

---

### Post by sisco311 on 2018-10-24
You should use the symlinks from /dev/disk/by-id/

For more details check out:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://wiki.archlinux.org/index.php/Persistent_block_device_naming](https://wiki.archlinux.org/index.php/Persistent_block_device_naming)

---

