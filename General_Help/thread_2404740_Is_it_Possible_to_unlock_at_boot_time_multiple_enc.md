---
title: "Is it Possible to unlock at boot time multiple encrypted devices; luks &amp; lvm2"
date: 2018-10-28
forum: General Help
---

### Post by cheetah2003 on 2018-10-28
So basically in most of my installations, I have a similar setup, a operating system SSD, and a larger slower HDD for data.

I use LVM for everything, layered onto LUKS style encrypted block devices.  Using crypttab, I identify my crypted devices via uuid and during system bootup from the only unencrypted part of the system /boot, I am asked to enter the passphrase to unlock my devices.

The kind of annoying part is, I get asked twice.  Once for the SSD, and once for the HDD, since they're separate devices.

There was one arrangement I had, kind of accidentally, but I haven't looked into it.  Once I installed the system so both the devices were separate volume groups in lvm; ie vg0 for the ssd, vg1 for the hdd.. and it seemed to decrypt both after only asking me for the password on the vg0 device (they both had the same passphrase, and vg1 wasn't needed to boot the system.  I don't even think I had anything on it at the time.)

However, my preferred setup is to have both the devices in one volume group so I can do mirroring between the HDD and SSD.  Since they both have the identical passphrase, I'm curious if there's some way to modify this boot up sequence so I only have to type the passphrase once and it'll apply it to both the devices?

---

