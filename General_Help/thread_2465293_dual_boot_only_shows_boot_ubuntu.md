---
title: "dual boot only shows boot ubuntu"
date: 2021-07-28
forum: General Help
---

### Post by m3t3ors on 2021-07-28
i just done a dual boot laptop for my daughter ubuntu 20..04  and linux mint 20.2
ubuntu was already installed about 3 weeks ago.
anyway the laptop has 2 hdd both 750g each.
first hdd is the os drives and 2nd she uses as her save hdd.

mint split the 1st hdd into 2 each 350g (ubuntu on the 1st half mint on the 2nd), after mint finished the installation on the reboot only ubuntu shows on the boot menu.

any help appreciated..

---

### Post by tea for one on 2021-07-28
Probably a good time to run [Boot-Repair 2nd Option](https://help.ubuntu.com/community/Boot-Repair)

It is generally better to post the link to the output of the report in this thread rather than run the automatic repair.

---

### Post by m3t3ors on 2021-07-28
The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

---

### Post by oldfred on 2021-07-28
Are both systems installed in UEFI boot mode? And with newer UEFI hardware, better to use UEFI, not old legacy/BIOS/CSM mode.
How you boot install media, UEFI or BIOS is then how it installs. And then in UEFI/BIOS you have to have system set to boot in that mode. 
Just always use UEFI.

If you post link to Summary Report from Boot-Repair, it will show details.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tea for one on 2021-07-29
@m3t3ors

The thread is marked as [COLOR="#0000FF"]solved[/COLOR].

Please post the solution as it will help other forum searchers/users.

---

### Post by m3t3ors on 2021-07-29
ok. i dont know if this helped but in bios for os mode selection i have 3 options
1, CSM OS
2 UEFI OS
3 CSM AND UEFI OS

i set to boot csm and uefi and installed mint first. then installed ubuntu and all works fine.

thanks for all help.

john

---

### Post by tea for one on 2021-07-30
Thank you for the info.

As you have solved the boot problem by enabling the BIOS option [COLOR="#000080"]CSM & UEFI[/COLOR], it seems that you may have mixed mode installations (as mentioned by [COLOR="#0000FF"]oldfred[/COLOR] in post 4)

In the event of a kernel/grub update in either OS, you may be back to square one (i.e. only one OS is instantly available).

I'm not suggesting that you change anything now, just be aware of possible future hazards.

---

