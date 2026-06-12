---
title: "boot-repair issue, ubuntu doesn't start after disk cloning"
date: 2022-06-07
forum: General Help
---

### Post by parmeg on 2022-06-07
Good afternoon everyone,
I just take my laptop from the assistance, where they cloned my old hdd into a new ssd drive.
I was supposed to have no struggles in restarting, but i discovered ubuntu doesn't run anymore.
Searching on the internet i tried to run boot-repair from a USB drive, here is the report. I can't understant what to do


[https://paste.ubuntu.com/p/McKTK5QJHW/](https://paste.ubuntu.com/p/McKTK5QJHW/)


Thanks in advance to everyone could help

---

### Post by oldfred on 2022-06-07
You have UEFI install but booted Boot-Repair in old BIOS mode.
Reboot in UEFI mode and rerun report as it will show more info on UEFI settings. You may just need to reinstall grub in UEFI mode to add a UEFI boot entry into UEFI. The clone would not have added a new correct entry into UEFI to boot install.

Make sure UEFI settings are set to UEFI, probably with UEFI secure boot off.

---

