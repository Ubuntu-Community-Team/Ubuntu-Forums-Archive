---
title: "Help needed with Boot Repair"
date: 2024-09-20
forum: General Help
---

### Post by tr1950 on 2024-09-20
I've been using Ubuntu Studio for perhaps a couple of years with no problems. Recently there have been problems booting. Sometimes the boot hangs with the Ubuntu logo and the rotating circle. Other times it boots into a menu (grub?) with various options - various versions of Ubuntu and a couple of memory test options. Choosing a version other than the top one often works (and is what I'm using right now). I've run Boot Repair, but the advice seems to be to ask for opinions here before letting it do anything other than producing a report. So, I'd be grateful for any advice - the Boot Repair report is here... [https://paste.ubuntu.com/p/NdH8HBgsnR/](https://paste.ubuntu.com/p/NdH8HBgsnR/)

Boot Repair seems to be suggesting that I change the boot to UEFI mode. Not sure what that is, or how to do it.

Grateful for any help!

---

### Post by dragonfly41 on 2024-09-20
The clues are in the report.

> BIOS/UEFI firmware: A30(4.6) from Dell Inc.This installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).

> Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 22.04.4 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. 
You may want to retry after changing it to UEFI mode.

I would power up again and look at BIOS settings. Switch off legacy mode (in BIOS) and switch to UEFI.
Optionally consider later installing [rEFInd]("https://www.rodsbooks.com/refind/") as a companion to normal grub.

I have Dell tower and I hold down F2 a few seconds after I see Dell powering up image Then amend BIOS settings (taking note of changes made).

Update grub when back working then you can choose between normal grub or rEFInd in BIOS boot order.

---

### Post by yancek on 2024-09-20
You have a Legacy install of Ubuntu and this method of booting has been used since before windows and dos existed.  Most newer computers use UEFI and in fact, many computers manufactured in 2020 and later do not have a Legacy option.  You have what appears to be an EFI partition (sda1) which you can see see on line 15 of boot repair.  You have a Legacy install so this is not used or needed.  If it were an EFI install, you would see a list of EFI boot files on that partition but there are none.

Line 70 shows your device is NOT GPT so the standard would be a Legacy install.  You can if you wish, do an EFI install of Ubuntu on a non-GPT drive as recommended by boot repair which will then put the necessary EFI boot files on sda1.

Your system is configured with the following entries in the /etc/defaul/grub file which means no menu will show on boot and the TIMEOUT is set to zero.  Change the first line (STYLE) to menu and the TIMEOUT to a reasonable number so that you see the menu on boot.  
> 156 GRUB_TIMEOUT_STYLE=hidden
157 GRUB_TIMEOUT=0 

---

### Post by tr1950 on 2024-09-21
Many thanks for the advice. I'll see if I can sort things out based on this.

---

