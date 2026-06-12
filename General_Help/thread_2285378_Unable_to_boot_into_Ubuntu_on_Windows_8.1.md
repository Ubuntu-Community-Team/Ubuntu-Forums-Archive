---
title: "Unable to boot into Ubuntu on Windows 8.1"
date: 2015-07-05
forum: General Help
---

### Post by asker3 on 2015-07-05
Hello,

I am unable to boot into Ubuntu on Windows 8.1 I'm trying to set up dual boot.

I have turned off fast boot, changed the UEFI settings, moved the USB boot order in the BIOS, tried using unetbootin to make a bootable USB drive.

Am at a dead end.

Thanks.

---

### Post by yancek on 2015-07-05
If you used unetbootin on your windows to create a bootable flash drive and set the flash to first boot priority, it would be helpful if you would indicate exactly what happens when you try to boot it to begin the install.

---

### Post by asker3 on 2015-07-05
Absolutely nothing happens. It just boots into Windows as usual.

---

### Post by oldfred on 2015-07-05
If you created flash drive as bootable, you should in UEFI see two boot options for flash drive, one clearly UEFI & name of flash drive and the other just the flash drive which would be a BIOS/CSM/Legacy boot. You want the UEFI boot option.

Some UEFI systems, require you to specifically authorize flash drive UEFI booting. That seems to be for security reasons. And a few more like Acer require you to set a password (never lose that) to get the option to authorize other systems.

---

### Post by asker3 on 2015-07-05
In the UEFI settings there are options to
"Clear Secure Boot Keys"
"Key Ownership"
Should either of those be changed?

---

### Post by oldfred on 2015-07-05
NO.

Default key is the Microsoft one and that is also used by Ubuntu. But if you have secure boot off, key is not used.
Modifying keys is very advanced. I just know enough not to modify them.

---

