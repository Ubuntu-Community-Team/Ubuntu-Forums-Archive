---
title: "Signing a custom kernel module"
date: 2018-05-25
forum: General Help
---

### Post by betazoid26 on 2018-05-25
Hi, I am trying to sign a custom kernel module. This is the background:
On my acer laptop, I can boot a regular installation of ubuntu only with secure boot on - I have to configure secure boot in the UEFI and choose a trusted EFI-file. And I have this new Wacom tablet with bluetooth. Without the newest driver, bluetooth does not work though. So I have compiled and installed the newest driver. I have tested it in a live system, which can indeed boot without secure boot. In a regular installation though, the wacom driver module is blocked by secure boot and the tablet does not work at all. So I have to sign the driver module. I am trying to follow these instrucitons:

[https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot](https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot)

Basically, I think I can do this. However, I do not know what to do at the end

```
sbsign --key MOK.priv --cert MOK.pem my_binary.efi --output my_binary.efi.signed
```

This line I have to change, but what do I have to write instead of "my_binary.efi", I mean what is the name of the wacom efi?

Thanks in advance for the help

b

---

### Post by Holger_Gehrke on 2018-05-25
Read the article again, slowly. That command is for signing a custom kernel or bootloader. If you only want to sign a kernel-module, the description ends just before the subheading "What about kernels and bootloaders ?".

Holger

---

### Post by betazoid26 on 2018-05-25
Still, what is the name of the wacom module? I guess it is not "module.ko". How do I find that out?

---

### Post by Holger_Gehrke on 2018-05-25
Use the live system in which the driver works and look at the loaded modules with 'lsmod'. The one you want should be among the ones loaded on the live system but not on the installed one.

Holger

---

### Post by betazoid26 on 2018-05-25
Thanks, Holger!

---

### Post by betazoid26 on 2018-05-25
I am wondering: If the signing is successful in the live-system, could I simply copy the signed driver/module (to a pendrive e.g.) and paste it into the regular installation (overwrite the unsigned driver)? I guess not, could I?

---

### Post by betazoid26 on 2018-05-25
Another question: I think I need to sign 2 files: the module for the wireless/blutooth tablet and the module for the USB tablet - if I only sign the bluetooth module I probably won't be able to use the tablet while it is charging. Right?

Never mint: according to lsmod it is only wacom.ko which is loaded

---

### Post by betazoid26 on 2018-05-25
Well, I have signed all wacom.ko-s in my system but I keep getting "required key not availabe"
The module does not load

---

### Post by betazoid26 on 2018-05-26
The trick was to always load the system with shim.

---

