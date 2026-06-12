---
title: "removeable disk and sd-card use same device"
date: 2007-10-30
forum: General Help
---

### Post by stephan0h on 2007-10-30
Hi,

Recently I've installed a removable disk in my pc for my backups. I added a line in /etc/fstab to mount it like this:

/dev/sdb1 /backupsystem auto nouser,atime,auto,ro,nodev,noexec,nosuid 0 0

Now I found sd-cards are not mounted anymore automatically. Still I can mount them manually like this:

sudo mount /dev/sdb1 /media/sdcard

I should say that my removeable disk is removed at the moment. Apparently the same device name is used for both devices, My wild guess is that this is also the reason why automount of sd-cards is not working anymore. Probably my configuration is faulty. How can I correct this?

Thanks,
Stephan

---

### Post by dcstar on 2007-10-31
> **stephan0h said:**
> Hi,

Recently I've installed a removable disk in my pc for my backups. I added a line in /etc/fstab to mount it like this:

/dev/sdb1 /backupsystem auto nouser,atime,auto,ro,nodev,noexec,nosuid 0 0

Now I found sd-cards are not mounted anymore automatically. Still I can mount them manually like this:

sudo mount /dev/sdb1 /media/sdcard

I should say that my removeable disk is removed at the moment. Apparently the same device name is used for both devices, My wild guess is that this is also the reason why automount of sd-cards is not working anymore. Probably my configuration is faulty. How can I correct this?

Thanks,
Stephan

You should not put entries for removable disks in fstab, the system is designed to automount all removable devices itself.

If you want your removable disk to always mount in a specific place, just give the partitions on the device labels and then they will always be mounted at: /media/label

---

### Post by stephan0h on 2007-10-31
Hi,

I've tried this but the disk is not automatically mounted in /media. Is it because my partition has no label? Or is this only working for usb-devices? (my disk is an sata-drive)

Furthermore I would like the disk to be mounted in /backupsystem not /media/<label> - and I want it to be mounted readonly.
Can't I somehome "reserve" the device even if the disk is not there?

regards,
stephan

---

### Post by stephan0h on 2007-11-09
luckily linux and thus also ubuntu is not such a monolithic system where adaptions are impossible. and i've found a solution for this problem: I've defined me an udev-rule.

I created this file:

/etc/udev/rules.d/10-local.rules

containing this rule:

KERNEL=="sdb1",SUBSYSTEMS=="scsi",      NAME="backupsystem"

and changed the entry in /etc/fstab to this:

/dev/backupsystem /backupsystem auto nouser,atime,auto,ro,nodev,noexec,nosuid 0 0

now my removable harddisk is correctly mounted and my sd-cards get automounted like they did before. brilliant!

and that's where my new knowledge comes from: [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

