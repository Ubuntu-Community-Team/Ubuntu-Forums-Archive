---
title: "Grub: start_image() returned Invalid Parameter (but still boots OK)"
date: 2021-12-02
forum: General Help
---

### Post by Paddy Landau on 2021-12-02
I'm curious about what this error message means, and if I should bother to do something about it.

**Installation**

[LIST]
[*]When I installed, I chose to wipe the entire drive and replace it with Ubuntu 20.04 with full-disk encryption. That means…
[LIST]
[*]A UEFI partition (/boot/efi when booted)
[*]A boot partition (/boot when booted)
[*]An encrypted partition using LUKS, and inside that LVM, containing just one partition for my entire system.
[/LIST]
[/LIST]
**What happens normally**

[LIST=1]
[*]When I boot, the system goes straight into the Grub prompt, where I can choose the default (continue into Ubuntu) or one of the recovery options.
[*]After continuing to Ubuntu or one of the recovery options, I'm asked for the LUKS passphrase.
[*]The boot continues correctly.
[/LIST]
**What's changed**

[LIST]
[*]Before getting to step 1, i.e. the Grub prompt, the following message flashes on the screen:
```
start_image() returned Invalid Parameter, falling back to default loader
```
[*]However, the system still works correctly, so I don't have a problem.
[/LIST]
**My questions**

[LIST=1]
[*]What does this error message mean?
[*]Is it advisable to do something about this, or would I be wasting my time?
[/LIST]
Thank you

---

### Post by VMC on 2021-12-03
[https://edk2-docs.gitbook.io/edk-ii-uefi-driver-writer-s-guide/5_uefi_services/readme.2/524_loadimage_and_startimage](https://edk2-docs.gitbook.io/edk-ii-uefi-driver-writer-s-guide/5_uefi_services/readme.2/524_loadimage_and_startimage)

I had some strange grub error. It turned out to be a UEFI folder that I no longer needed. I cleaned up the UEFI folders to reflect only what is installed and the error went away.

---

### Post by Paddy Landau on 2021-12-03
> **VMC said:**
> [https://edk2-docs.gitbook.io/edk-ii-uefi-driver-writer-s-guide/5_uefi_services/readme.2/524_loadimage_and_startimage](https://edk2-docs.gitbook.io/edk-ii-uefi-driver-writer-s-guide/5_uefi_services/readme.2/524_loadimage_and_startimage)
I had some strange grub error. It turned out to be a UEFI folder that I no longer needed. I cleaned up the UEFI folders to reflect only what is installed and the error went away.
Thank you. The link is a little over my head, unfortunately. I wouldn't know where to start cleaning up UEFI folders, so I shan't do it lest I break Grub!

---

### Post by VMC on 2021-12-03
Do a ```
sudo ls -la /boot/efi/EFI
``` so we see what's in there.

---

### Post by Paddy Landau on 2021-12-04
Here we are:
```
[COLOR=#000080]$ sudo ls -lA /boot/efi/EFI[/COLOR]
total 12
drwx------ 2 root root 4096 Sep  5  2020 BOOT
drwx------ 4 root root 4096 Nov  1 07:53 Dell
drwx------ 3 root root 4096 Sep 17 07:22 ubuntu

[COLOR=#000080]$ sudo ls -lA /boot/efi/EFI/BOOT[/COLOR]
total 1860
-rwx------ 1 root root 955656 Aug 21 08:09 BOOTX64.EFI
-rwx------ 1 root root  85672 Aug 21 08:09 fbx64.efi
-rwx------ 1 root root 856232 Aug 21 08:09 mmx64.efi

[COLOR=#000080]$ sudo ls -lA /boot/efi/EFI/Dell[/COLOR]
total 8
drwx------ 3 root root 4096 Sep 17 07:26 Bios
drwx------ 2 root root 4096 Nov  1 07:53 logs

[COLOR=#000080]$ sudo ls -lA /boot/efi/EFI/ubuntu[/COLOR]
total 3548
-rwx------ 1 root root     108 Aug 21 08:09 BOOTX64.CSV
drwx------ 2 root root    4096 Sep 17 07:22 fw
-rwx------ 1 root root   62024 Jul 26 08:50 fwupdx64.efi
-rwx------ 1 root root     112 Aug 21 08:09 grub.cfg
-rwx------ 1 root root 1734528 Aug 21 08:09 grubx64.efi
-rwx------ 1 root root  856232 Aug 21 08:09 mmx64.efi
-rwx------ 1 root root  955656 Aug 21 08:09 shimx64.efi
```

---

### Post by VMC on 2021-12-04
That looks normal. Does your error look like this guy's?
[https://githubmemory.com/repo/rhboot/shim/issues/370](https://githubmemory.com/repo/rhboot/shim/issues/370)

---

### Post by Paddy Landau on 2021-12-04
> **VMC said:**
> That looks normal. Does your error look like this guy's?
No. It's just the one message, by itself, on the screen. It shows for just a second or two, then the normal Grub screen replaces it.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289589&stc=1[/IMG]

---

