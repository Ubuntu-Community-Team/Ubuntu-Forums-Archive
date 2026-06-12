---
title: "SCSI Devices changing with every reboot"
date: 2013-02-12
forum: General Help
---

### Post by daniel borg on 2013-02-12
Hi

I've built an Ubuntu 12.04 machine and everything seems to be working  fine apart from one thing, it would appear as if the SCSI Devices change  ID with every reboot, with redhat and fedora SCSI Device IDs remain  static after a reboot but not with ubuntu, the IDs appear to be  dynamically assigned.

Has anyone come across this before and if so is there a way to fix it?

Thanks

Dan

---

### Post by dcstar on 2013-02-14
> **daniel borg said:**
> Hi

I've built an Ubuntu 12.04 machine and everything seems to be working  fine apart from one thing, it would appear as if the SCSI Devices change  ID with every reboot, with redhat and fedora SCSI Device IDs remain  static after a reboot but not with ubuntu, the IDs appear to be  dynamically assigned.

Has anyone come across this before and if so is there a way to fix it?


If you are referring to drive devices (/dev/sda /dev/sdb etc.) then this has been the way for over 5 years now.

UUIDs for partitions are supposed to be used instead of these changeable designations.

---

