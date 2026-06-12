---
title: "Please help. Write error on boot"
date: 2016-12-12
forum: General Help
---

### Post by nyd59 on 2016-12-12
Using 16.04. On boot, i get the following error

Sh: write error: device or resource busy

I have gone into the grub command menu to try and fix the error. However, using the ls command yields another error:

Secure boot forbids loading module from (hd0,gpt1)/boot/grub/x86_64-efi/ls.mod

So I cannot tell what is causing the error.

Please can someone explain how to fix this. Please understand I am very new to Linux so basic steps please!

---

### Post by ajgreeny on 2016-12-12
I assume this is a dual boot with secure boot turned on in the UEFI?

If so you should start by disabling secure boot which should then allow the loading of that module. You should also disable fast start in Windows if you have not already done so or you will have major problems dual booting the two OSs.

---

### Post by nyd59 on 2016-12-12
It is dual boot, but windows does not work. Hence Linux (which had been working fine for a few months).

Have disabled secure boot. Ls  now yields:

(hd0) (hd0,gpt9) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (cd0) error: failure reading section 0x0 from 'cd0'

---

