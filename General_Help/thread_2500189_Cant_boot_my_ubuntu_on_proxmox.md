---
title: "Cant boot my ubuntu on proxmox"
date: 2024-08-26
forum: General Help
---

### Post by chiliasmstudio on 2024-08-26
I'm having trouble booting my existing Ubuntu VM on Proxmox. The VM was working fine until recently, but now it won't boot.


Here are the details:


Proxmox Version: PVE 8.2.4
Ubuntu Version: Kubuntu 24.04 LTS
Error Message: [Ubuntu Pastebin]("https://paste.ubuntu.com/p/rBnVVzKKnR/")
Steps Taken:
I have checked the boot order.
Verified disk integrity.
Followed the steps in this guide to recover the partition table: [How to recover lost partition in Linux (simplified.guide)]("https://www.simplified.guide/linux/disk-recover-partition-table")

---

### Post by Rubi1200 on 2024-08-26
Did you run the boot info script before or after using Testdisk?

Did Testdisk find anything?

Line 12: Mounting failed:   mount: /mnt/BootInfo/sda1: mount(2) system call failed: Structure needs cleaning

Line 16: 0 OS detected

You might want to try running e2fsck on the unmounted filesystem from a live USB.

---

### Post by chiliasmstudio on 2024-08-26
After checking and trying various solutions, it seems that the filesystem is entirely corrupted, and even mounting it does not allow us to read the complete data. Therefore, I have decided to restore from a backup.

---

