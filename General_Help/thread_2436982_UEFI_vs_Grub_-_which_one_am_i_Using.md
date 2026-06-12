---
title: "UEFI vs Grub - which one am i Using?"
date: 2020-02-16
forum: General Help
---

### Post by yaminb on 2020-02-16
Background:
I was planning to get an SSD to speed up booting and saw various way of copy the files and adding grub to the drive...
For example: [https://www.pcsuggest.com/hdd-to-ssd-cloning-linux/](https://www.pcsuggest.com/hdd-to-ssd-cloning-linux/) This then let me into whether I need to do anything special for UEFI and then I wondered what do I even have.

Question:
Anyways, in the interest of one question per thread, I got myself confused on whether I have grub or UEFI. I'm probably missing something in my understanding here.
It looks to me like I have UEFI enabled.

```

/sys/firmware/efi$ ls
config_table  fw_platform_size  runtime      systab
efivars       fw_vendor         runtime-map  vars

/sys/firmware/efi$ sudo efibootmgr 
BootCurrent: 0003
Timeout: 5 seconds
BootOrder: 0003,0000,0001,0002
Boot0000* Windows Boot Manager
Boot0001* Hard Drive 
Boot0002* CD/DVD Drive 
Boot0003* ubuntu

```

Yet, when I boot my Ubuntu, it definitely goes to a grub menu and I can see the relevant entries in:
/boot/grub/grub.cfg


I'm thinking the way I have this setup is UEFI is enabled and letting me boot to my drive of choice. If I choose Ubuntu, then grub takes over  and I can choose the boot again?

Thanks,

---

### Post by CatKiller on 2020-02-16
You'll be using Grub either way.

The distinction is between UEFI/GPT or BIOS/MBR. 

The simplest way is that the background of the Grub menu is purple if you're using BIOS and black if you're using UEFI.

---

### Post by sgage on 2020-02-16
By the time you see the grub menu, UEFI has already done its job. It is not UEFI vs. grub UEFI hands off to a bootloader/manager, which might be grub or windows or whatever.

---

### Post by Bashing-om on 2020-02-16
yaminb; Hello -

What shows from terminal command:
```

[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"

```

[INDENT]/sys knows everything
[/INDENT]

---

### Post by Skaperen on 2020-02-16
UEFI *then* GRUB, not the other way around.

---

