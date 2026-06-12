---
title: "PC doesn't boot anymore"
date: 2024-08-29
forum: General Help
---

### Post by yassern11 on 2024-08-29
Hello everyone,
I have a dell g5 15. I removed Nvidia drivers and reinstalled them without reboot. My laptop doesn't boot anymore. This is the boot-repair report. (From usb live) [https://paste.ubuntu.com/p/pVqqcBNqSB/](https://paste.ubuntu.com/p/pVqqcBNqSB/)
Please help me.

---

### Post by oldfred on 2024-08-29
Your nvme0n1p2 is confused.
It shows in some places as FAT32 with boot files and others as a Microsoft reserved. The Microsoft reserved is required by Windows before first NTFS partition with an install and must be unformatted not FAT32. And usually smaller or 132MB.

Otherwise boot looks normal, but if you have nVidia driver issues may be best to purge & reinstall.
Can you boot recovery mode or second kernel in grub menu?

---

### Post by tea for one on 2024-08-29
Line 187 - /dev/nvme0n1p3              1.8G  95% /mnt/boot-sav/nvme0n1p3
Your Ubuntu partition only has 5% free space.
I would use a live session to transfer rarely used data to another disk.
Then, remove unnecessary programs, logs etc.

---

### Post by yancek on 2024-08-29
>  Your Ubuntu partition only has 5% free space.

Going into the /var/log directory and deleting old files should help.

---

### Post by oldfred on 2024-08-30
System was/is pre-installed Ubuntu.
The p2 partition  has a grub boot & must have ISO to restore system.
Not sure why p2 would be set as Microsoft Reserved. That is only for Windows and is an unformatted partition.
Perhaps a way to hide partition, so user does not see a FAT32 partition and try to use it?

One entry in UEFI 0001 uses partUUID/GUID of p2 to boot a bootx64.efi which probably is customized for recovery.
And you have modified grub with added boot stanza to boot recovery mode on p2.

Line 210 has grub menu to boot ISO & restore system.
> Install Complete, remove media and reboot.
Dell Recovery


And the Dell Recovery entry line 274 uses UUID of p2 and has a grub loop mount type entry to boot an ISO.
Not sure if then any of the options add features unique to Dell version.
But usually if Dell needs updated drivers they get added into later releases of kernel & distributions.

---

### Post by yassern11 on 2024-08-30
Thank you for your response. Unfortunately the problem persists[COLOR=#000000][FONT=Arial] 
I tried to reinstall grub with boot-repair but no changes. I then tried to do it manually using command line "efi partition nvme0n1p1" and linux partition nvme0n1p3 with binding proc sys and efi folders, then i used chroot to install grub. I purged nvidia drivers and reinstall them automatically. I tried to change prime-invidia (chroot) to intel. i tried to fix packages dependencies...
I tried nomodeset
....
I free up disk space I have more than 50GB now 
the last boot-repair report     [https://paste.ubuntu.com/p/3RGHvmVFXv/](https://paste.ubuntu.com/p/3RGHvmVFXv/)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] I always get boot stuck with _
[/FONT][/COLOR]

---

### Post by yassern11 on 2024-08-30
I tried to use dell assist from bios but I quit when I found that recovery will reset my files and installed software.
I checked hardware, it's 100% ok
in boot sequence, I found 2 options quiet similar:
UBUNTU
UEFI PC SN530 NVMe WDC 512GB 2043D9810607 1
UEFI PC SN530 NVMe WDC 512GB 2043D9810607 1 2

the problem is still there

---

### Post by oldfred on 2024-08-30
Are you getting just _ or grub>  ?

If just _, you probably are booting but then some issue after grub.

Can you boot to grub menu?
Press escape right after Dell logo & before grub menu would normally appear. Sometimes have to try more than once.
Or you may have to turn off fast boot in UEFI to have time to press any key.

Then at grub menu can you boot recovery mode to command line?
Or does it show errors on loading a driver? Often last line shown is not issue, but several lines above that.

---

### Post by yassern11 on 2024-08-30
It gives me just _
these are pictures for more details. 
[[img]https://i.postimg.cc/fkpr4zvX/20240830-171458.jpg[/img]](https://postimg.cc/fkpr4zvX)

[[img]https://i.postimg.cc/k6hhgq30/20240830-171501.jpg[/img]](https://postimg.cc/k6hhgq30)

[[img]https://i.postimg.cc/T5LNyFTp/20240830-171515.jpg[/img]](https://postimg.cc/T5LNyFTp)

[[img]https://i.postimg.cc/qgz5Zh24/20240830-171529.jpg[/img]](https://postimg.cc/qgz5Zh24)

[[img]https://i.postimg.cc/FdKBv1qb/20240830-171540.jpg[/img]](https://postimg.cc/FdKBv1qb)

[[img]https://i.postimg.cc/PLyR016r/20240830-171545.jpg[/img]](https://postimg.cc/PLyR016r)

---

### Post by oldfred on 2024-08-30
Because you are getting grub menu & recovery mode, you are technically booting.
But usually some sort of driver issue, most often video related, but could be something else.

Does booting older kernel work?

Have you tried the various options in the recovery mode.
I might try fsck first as system has to be unmounted/read only for that to work.
Then enable network & try the various update options.

---

### Post by yassern11 on 2024-08-30
Thank you very much.
It works now :P. I choose the oldest kernel oem.
Thank you again for your assistance.

---

