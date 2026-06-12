---
title: "Dual boot uefi problem"
date: 2021-10-06
forum: General Help
---

### Post by stanstanstan on 2021-10-06
Hi,

I had a dual boot windows 8.1 / xubuntu 18.04 (UEFI) working just fine until last week on a Dell M3800 Laptop.
After some obscure update I cannot access my grub any more and my laptop automatically boot on Windows (fast boot is disabled).
I run boot-repair and the boot-info file can be found here:

[https://paste.ubuntu.com/p/SrnCqHvR5t/](https://paste.ubuntu.com/p/SrnCqHvR5t/)

Can someone help me, I don't know how to proceed to fix my boot.

Many thanks in advance

---

### Post by Impavidus on 2021-10-06
Both Ubuntu and Windows appear to be properly installed, both having a bootloader in the EFI partition on drive sda. Maybe Windows installed an update and changed UEFI settings to boot Windows by default. See if changing UEFI settings helps.

---

### Post by tea for one on 2021-10-06
> **stanstanstan said:**
> 
After some obscure update I cannot access my grub any more and my laptop automatically boot on Windows 

Windows update or Xubuntu update?

[COLOR="#0000FF"]Line 442[/COLOR] - If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.

Have you tried to boot Xubuntu from the UEFI boot menu?

---

### Post by stanstanstan on 2021-10-06
> **Impavidus said:**
> Both Ubuntu and Windows appear to be properly installed, both having a bootloader in the EFI partition on drive sda. Maybe Windows installed an update and changed UEFI settings to boot Windows by default. See if changing UEFI settings helps.

Which settings ? I tried changing UEFI order available during bios loading but without success.

---

### Post by stanstanstan on 2021-10-06
> **tea for one said:**
> Windows update or Xubuntu update? 

no idea ... I did a couple of updates first on Xubuntu and later on Windows and tada no more Xubuntu.

[COLOR=#0000FF]> **tea for one said:**
>  Line 442[/COLOR] - If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.

Have you tried to boot Xubuntu from the UEFI boot menu?

I tried and it does not work.

Being clueless about uefi, I tried to add some boot option using :
- /UEFI/ubuntu/bootx64.efi
- /UEFI/ubuntu/shimx64.efi
- /UEFI/ubuntu/grubx64.efi

none of the above worked.

I also see two "Windows boot manager" entries in the uefi boot option of the bios (no idea why).

---

### Post by Cavsfan on 2021-10-06
> **stanstanstan said:**
> Which settings ? I tried changing UEFI order available during bios loading but without success.

BIOS has an option to set which system it boots from. It will be separate from the order of availability, but both should be set to the same. I have to get into advanced mode, select boot and scroll down to it.

I have Arch Linux, Fedora 34 and 3 Xubuntu systems. My grub is on Fedora and I was able to restore it to Fedora via BIOS after another system's grub installed and took over the boot process.

Edit: I also have Windows 10

---

### Post by tea for one on 2021-10-06
> **stanstanstan said:**
> 
Being clueless about uefi, I tried to add some boot option using :
- /UEFI/ubuntu/bootx64.efi
- /UEFI/ubuntu/shimx64.efi
- /UEFI/ubuntu/grubx64.efi

Where did you try to add these options?
Do you have an EFI shell facility in your firmware?

You have Windows installed on sda and Xubuntu on sdb, therefore with UEFI, you should have a boot menu to select either disk?

Alternatively, you could remove (de-activate or isolate) sda and see if sdb boots?

---

### Post by tea for one on 2021-10-06
> **stanstanstan said:**
> no idea ... I did a couple of updates first on Xubuntu and later on Windows and tada no more Xubuntu.

If Windows was the last update, sometimes Fast Start Up is re-enabled without user intervention.
Might be worth double-checking?

---

### Post by stanstanstan on 2021-10-07
> **tea for one said:**
> Where did you try to add these options?
Do you have an EFI shell facility in your firmware?

You have Windows installed on sda and Xubuntu on sdb, therefore with UEFI, you should have a boot menu to select either disk?

Alternatively, you could remove (de-activate or isolate) sda and see if sdb boots?

Yes I have a EFI shell facility to edit these options before boot.

I tried to boot select either disk on the boot menu but selecting ubuntu redirect me to windows.

I will try to de-activate/isolate sda.

---

### Post by stanstanstan on 2021-10-07
> **tea for one said:**
> If Windows was the last update, sometimes Fast Start Up is re-enabled without user intervention.
Might be worth double-checking?

triple-checked, it's still off

---

### Post by stanstanstan on 2021-10-07
Out of idea I run the automatic repair of boot-repair.
It reinstalled grub, edited the EFI and I got back my dual boot.

So everything worked fine.

Thanks for your help and suggestions!

---

