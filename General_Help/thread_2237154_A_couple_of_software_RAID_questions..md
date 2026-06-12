---
title: "A couple of software RAID questions."
date: 2014-07-31
forum: General Help
---

### Post by cjsmall on 2014-07-31
I am in the process of replacing an aging Sun server with a custom built Intel system that will run Xubuntu and KVM, and have a few question concerning the configuration and use of software-based RAID on the new system.

On my current system I have pairs of RAID-1 mirrored disks.  For each pair, in a hot-swap bay I install a third disk that is manually "attached" to the existing RAID array using the Solaris cfgadm and meta-commands.  This is allowed to sync up with the mirror and is then "detached", removed from the system and stored off site.  I would like to do something similar with the new system and plan
to use a case that has a couple of hot-plug docks.  I have looked at the Ubuntu **mdadm(8)** command and it seems as though this should be possible, but I have no direct experience to recognize any limitations I might run into.  My questions:

1: The SATA devices on the motherboard are controlled by different devices which limit hardware RAID (fakeRAID?) to only those devices sharing the same controller.  I assume that at the OS level this will not be a consideration and that any attached drive can be configured into an array regardless of the underlying hardware controller.  Is this correct?

2: For the boot device, I plan to install (2) SSDs which will be mirrored.  Are there any issues with GRUB or OS upgrades or KVM virtualization when using a software-based mirror on the primary disk?

3: For purposes of the mirrored backup discussed above, would there be any problems with temporarily attaching a HDD to the SSD mirror?  If the HDD was larger than the SSDs would the fact that it wasn't an identical device play havoc with the RAID mirror?

Thanks for any insights you can offer.  I would like to get a grasp of any potential problems before ordering the hardware.

---

### Post by stephenmichaelphotography on 2014-07-31
1. Correct.  This is one of the big advantages of software RAID.

2. There sure are, but they're easily remedied.  Basically, /boot needs to be on either a hardware RAID or a single physical drive.  However, /boot is fairly small, and it would be trivial to add a storage medium capable of holding it.  On my system, it is less than 200MB, and it's not something that needs any particularly special backup.  A tiny/cheap drive would suffice.  I don't think there'd be any other issue, but I'm sure someone will chime in if I'm forgetting something or sharing out dated info.

3. Nope, wouldn't cause any issue at all.  You just wouldn't be able to take full advantage of the drive's storage capacity, for obvious reasons.

---

### Post by cjsmall on 2014-08-01
> **stephenmichaelphotography said:**
> 2. There sure are, but they're easily remedied.  Basically, /boot needs to be on either a hardware RAID or a single physical drive.  However, /boot is fairly small, and it would be trivial to add a storage medium capable of holding it.  On my system, it is less than 200MB, and it's not something that needs any particularly special backup.  A tiny/cheap drive would suffice.  I don't think there'd be any other issue, but I'm sure someone will chime in if I'm forgetting something or sharing out dated info.

Thank you for the reply.  It was very helpful.  I have a couple follow up questions.

If /boot must be separated from the rest of the OS, then what is the partitioning strategy for a bare metal installation of the entire Ubuntu server/mirroring.virtualization software system and how is the boot loader configured?

Let's say you are installing the OS onto a pair of mirrored large format SSDs.  I assume that the initial OS installation would be to a single SSD, after which the second mirrored disk would be configured.  Now, I'm not clear what happens to /boot?  Is it then copied to an external HDD and somehow mounted to the OS?  What then happens during package updates or upgrades to the next rev of the OS?  Does the SSD mirror need to be broken for certain operations or can upgrades be performed on the intact mirror?

I there are documents that discuss these issues, I would really appreciate pointers to them.

---

