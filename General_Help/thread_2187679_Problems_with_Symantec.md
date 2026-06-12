---
title: "Problems with Symantec"
date: 2013-11-13
forum: General Help
---

### Post by dave2001 on 2013-11-13
I have a Thinkpad T430s supplied by my employer, which is on permanent loan to me., and unfortunately I only have user level access to the system. It is unbelievably irritating to have a gimped computer that I could turn into a nicely running machine, if only I could get administrative privileges. Given that our tech department is woefully inadequate to even the simplest tasks, I decided to put Kubuntu on the lappy as well, so I have an OS for personal use that doesn't make me tear my hair out. I do have to use the windows installation for some tasks, as our company uses a proprietary software that is Windows only, so getting rid of the windows install completely is a no-no.
To make a dual boot system, i have replaced the optical drive with a second HDD caddy. This is the only way to make a dual-boot, because the internal disk is entirely encrypted with Symantec PGP Whole Disk Encryption.

My problem is this: I cannot get grub to recognize that there is another operating system, so it boots straight into Kubuntu. Editing the Windows boot menu isn't an option, because i don't have administrator level access. I can use the bios to choose which OS to boot, but I'd really rather use grub.  It seems I just need to know where to point grub for the Symantec pre-boot process to begin.

Any ideas greatly appreciated!

---

### Post by Bucky Ball on 2013-11-13
You could try running boot repair or in a terminal in Kubuntu, run:

```
sudo update-grub
```

Reboot. 

Also, you mean you are not getting a menu at boot to select an OS? Try holding down the shift key directly after boot. That should take you to a menu. If it doesn't, open a terminal in Kubuntu, paste this in:

```
sudo nano /etc/default/grub
```

... and look for this line:

```
Grub_Timeout = 0
```

Change it to:

```
Grub_Timeout = 10
```

Reboot.

---

### Post by grahammechanical on 2013-11-13
The update-grub command should produce a list of operating systems that Grub OS-Prober has found. If it does not find the Windows OS, then you may have to accept that Grub cannot read the encrypted disk. Surely that is the purpose of encrypting a disk or partition. At least you are not prevented from loading Kubuntu.

Regards

---

### Post by dave2001 on 2013-11-16
Thanks for the suggestions. Yes, i've already tried updating grub so that it generates a new config file which should contain any other OS's it detects. The problem is that grub is not detecting the windows installation. There are no other entries on the grub selection menu. This is no doubt, as grahammechanical surmised, because the HDD containing windows is encrypted. 

When grub has an entry for another OS, it's really just pointing to that  OS's boot-loader (if I understand the process correctly). I believe there must be some way to use grub to start the encrypted windows install. There is obviously enough un-encrypted information for the the bios to pass the boot process along to the Symantec PGP login. So what I really need is a way to identify where the data for the Symantec pre-boot login is, and how to have grub point to it.

---

### Post by tgalati4 on 2013-11-16
I would guess that GRUB has problems reading an encrypted Windows partition.  Have you tried to manually edit the grub menu using the* chainloader +1* entry?

[https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)

---

### Post by dave2001 on 2013-11-17
> **tgalati4 said:**
> I would guess that GRUB has problems reading an encrypted Windows partition.  Have you tried to manually edit the grub menu using the* chainloader +1* entry?

[https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)

This is just the sort of thing I was looking for! Thanks, I'll give it a shot.

---

### Post by philinux on 2013-11-17
I would stick with the bios boot method. Like you said the machine is technically not yours.

---

