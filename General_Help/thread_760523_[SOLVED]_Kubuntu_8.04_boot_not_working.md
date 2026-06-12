---
title: "[SOLVED] Kubuntu 8.04 boot not working"
date: 2008-04-20
forum: General Help
---

### Post by UltimateSephiroth on 2008-04-20
Hi! I'm UltimateSephiroth and I'm relatively new person when it comes to Linux. I decided to finally install a Linux distro on my hard drive, and heard about this WUBI system. It sounded very good to me, and I downloaded the program. Next I ran the program and set the following values:

Installation drive: D: (38 GB free)
Installation size: 8 GB
Desktop environment: Kubuntu (KDE3.5 version)
Language: Finnish
Username: tomi
Password: doesn't matter and even if it did, I'd fake it

WUBI downloaded the package well and it seemed to install the necessary files too without a problem. Then it was about time to reboot. So I did. That screen where you can choose the OS appeared, and I choose 'Kubuntu'. Everything up to this point went well, but the boot didn't turn out as it should've been. This is the error I got, word-by-word:

[FONT="Fixedsys"]kernel /ubuntu/install/boot/vmlinuz boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-amd64.iso quiet splash ro automatic-ubiquity locale=fi_FI.UTF-8 noprompt --

Error 13: Invalid or unsupported executable format[/FONT]

Computer details:
Processor: AMD Turion 64 x2 TL-56 (1.8 GHz)
Video card: NVidia GeForce 7000M
RAM: 2GB DDR2
The other OS beside Kubuntu: Microsoft Windows Vista Home Premium SP1 FIN
Hard disks' file system: NTFS

Please help as soon as possible. Thanks :)

E: The WUBI executable was Wubi-8.04-beta-rev487.exe, if that's an important thing to know.

E2: I can open D:\ubuntu\install\hardy-desktop-amd64.iso successfully without errors in WinRAR under Vista, so it's probably not at least a corrupted file transfer problem.

E3: The file actually WAS corrupted (MD5 should've been c754c8a8805f59cd9607686bd901340f; it was 64B46A4B16E8CFA61142CD33F2DD154A). Thread can be closed now.

---

### Post by ago on 2008-04-20
That's usually due to a bad ISO
Please uninstall, delete the ISO from ubuntu-backup, redownload the ISO manually, check the md5sum and retry

---

### Post by ago on 2008-04-20
> **ago said:**
> That's usually due to a bad ISO
Please uninstall, delete the ISO from ubuntu-backup, redownload the ISO manually, check the md5sum and retry

Ah didn't read your last line!

---

