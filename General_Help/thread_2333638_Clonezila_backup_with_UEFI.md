---
title: "Clonezila backup with UEFI"
date: 2016-08-11
forum: General Help
---

### Post by deepakdeshp on 2016-08-11
Hello
I have an HP laptop set up as dual boot with windows 10 and ubuntu 16.04 in UEFI mode. I did not backup with clonezilla before installing Ubuntu.
Will i be sucessful in restoring ubuntu and windows sucessfully if I take a clonezilla backup of the full disk?
Any help is appreciated.

---

### Post by howefield on 2016-08-12
> **deepakdeshp said:**
> Hello
I have an HP laptop set up as dual boot with windows 10 and ubuntu 16.04 in UEFI mode. I did not backup with clonezilla before installing Ubuntu.
Will i be sucessful in restoring ubuntu and windows sucessfully if I take a clonezilla backup of the full disk?
Any help is appreciated.

Doesn't appear to be any reason why you wouldn't be successful, is there something that makes you think it wouldn't be ?

You can take an image of each partition separately (helpful if you only want to restore one of the operating systems) or of the whole disk. Or both :)

Just make sure that you get the right release of Clonezilla and that you have it check the image for restorabilty - part of the default wizard options.

> All versions of Clonezilla live support machine with legacy BIOS. If your machine comes with uEFI secure boot enabled, you have to use AMD64 version of alternative (Ubuntu-based) Clonezilla live.


---

### Post by deepakdeshp on 2016-08-13
>  
All versions of Clonezilla live support machine with legacy BIOS. If your machine comes with uEFI secure boot enabled, you have to use AMD64 version of alternative (Ubuntu-based) Clonezilla live. 
Thank you. How to check if machine is with secure boot enabled?

---

### Post by howefield on 2016-08-13
> **deepakdeshp said:**
> Thank you. How to check if machine is with secure boot enabled?

Hmm, not really sure to be honest, found this answer which seems to work..

```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

In any event, if you use the UEFI enabled Clonezilla, it will work regardless of how the machine is booting, it is only a problem if you download the non UEFI Clonezilla and try it on a machine that is using UEFI.

---

### Post by deepakdeshp on 2016-08-20
Thank you for the help.

---

### Post by RobGoss on 2016-08-20
> **deepakdeshp said:**
> Thank you. How to check if machine is with secure boot enabled?

You can always go into your **BIOS settings,** and see if secure boot is in fact enabled, depending on the machine I can hit **F-12 **to bring up my BIOS settings and from there I can navigate to the necessary options

---

