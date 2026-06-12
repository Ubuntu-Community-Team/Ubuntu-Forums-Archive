---
title: "[SOLVED] Mount when hotplugging"
date: 2007-09-19
forum: General Help
---

### Post by Bothered on 2007-09-19
I have an external firewire hard drive that I use only for backups. I have created an entry for the hard drive in /etc/fstab to mount the hard drive to /backup if it is turned on on boot. However, if I turn the hard drive on when the system is running I have to manually mount the drive (sudo mount -a). Is there any way to automatically mount the external drive to /backup if I turn it on while my system is running?

Also, is there a way to configure /etc/fstab so fsck only checks the external drive if it is turned on? At the moment any option other than "0" in the sixth column prevents my computer from booting.

---

### Post by catanzag on 2007-09-19
I've a multipartitioned firewire HD, but I didn't need to modify /etc/fstab, I mount/umont like an external USB drive, turning it on/off whenever I want. Didn't this work for you?

---

### Post by Bothered on 2007-09-19
Fraid not, as I want the drive to mount to a specific folder.

---

### Post by catanzag on 2007-09-19
OK in this case, you can write some udev rules to automatically mount in your chosen directory when hotplugged. There are somewhere in /etc/udev.d (more or less ;), I'm not on my linux box, so I cannot check the exact path), you can get them like examples. Some docs about udev can be found in [http://kernel.org//pub/linux/utils/kernel/hotplug/](http://kernel.org//pub/linux/utils/kernel/hotplug/). Hope it can help you.

---

### Post by Bothered on 2007-09-19
I can't seem to make any headway from the link you gave me. Can you recommend something a bit less heavy duty?

Incidentally, internet searching suggests I should configure hal for this. Any tips on how I might do this?

---

### Post by catanzag on 2007-09-19
Sorry, but as far as I know udev rules work fine for this issue (I did in the past), I don't know how to configure hal. 
I checked and the rules are in /etc/udev/rules.d, and are divided for class of devices. You can also find some other documentation under /usr/share/doc/udev or, for instance, in [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html). Sorry for not fullfill your need.

regards

catanzag

---

### Post by Bothered on 2007-09-22
I changed the mount options for the partition (in /etc/fstab) to defaults, noauto,user and no the drive mounts to the correct point when hotplugging.

I know that this implies noexec, but that's fine as this is only a backup partition.

---

