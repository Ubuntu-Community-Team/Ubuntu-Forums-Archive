---
title: "Unable to boot - no luck with boot-repair"
date: 2012-11-17
forum: General Help
---

### Post by N0thingman on 2012-11-17
Hi,
I'm running a basic LAMP server on Ubuntu 11.10 which has all of a sudden decided not to boot. I've got the system running with a bootable USB containing the same version and have attempted boot-repair a number of time without any luck (apart from it removing Grub).

Boot-repair opens and runs the first step, then it pops up a list of commands to install Grub, this is where dpkg returns with error code 1 so I cannot proceed past there. The output from Boot-Repair is [http://paste.ubuntu.com/1364344/](http://paste.ubuntu.com/1364344/) so from what I can tell its having trouble reading a disk in the system.

I have 2 disks, a SSD 50Gb and then a 500Gb platter for data storage, I can see all the information on the 50Gb disk (apart from the /var/www/ directory) so I'm going to assume the second hard drive has failed and due to the operating system running accross both disks this is causing my boot issue.

Preamble out of the way, 2 questions;

1. Would it be possible to get that smaller drive up and running somehow, just so that I can access mysql and run some backups?
2. Is a full system restore still on the cards or should I bite the bullet and restore from my backups (which are a couple of months old (yes yes I know)) so at least the site is back up and running?

I do lose a considerable amount of pages going the clean format and restore route however they can all be put back in, article by article from the original material.

I am currently downloading Rescatux (Super Grub Disk) to give that a shot as well.

---

### Post by YannBuntu on 2012-11-17
hello

> **N0thingman said:**
> Boot-repair opens and runs the first step, then it pops up a list of commands to install Grub, this is where dpkg returns with error code 1 so I cannot proceed past there.

if i were you, i would try to fix dpkg via an Ubuntu disk this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by N0thingman on 2012-11-17
Thanks so much for the reply, I've given that a shot however the install disk was unable to reinstall the operating system on the existing partitions even though the options were available. I've decided to bite the bullet and reinstall from scratch and then restore manually.

---

