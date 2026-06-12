---
title: "Do Ubuntu software updates touch EFI partition?"
date: 2013-03-13
forum: General Help
---

### Post by geohei on 2013-03-13
Hi.

Are Ubuntu software updates (apt-get update, upgrade) also updating files of the EFI partition (/boot/EFI)?

I ask because I'd like to image backup Ubuntu system partition only. Depending whether updates also touch EFI partition or not, I also need to backup that one on top of the Ubuntu system partition.

I have an initial image backup of both (done right after fresh install of Ubuntu), EFI and Ubuntu system partitions.

I.a.w. ... do I need to include the EFI partition in my weekly Ubuntu system partition image backups because it's files may change due software updates?

Thanks,

---

### Post by oldfred on 2013-03-13
The only things in the efi partition are the grub boot files. So an update to grub may write a new file to:
 /boot/efi/EFI/ubuntu/grubx64.efi

Not much else would write to that, so I might just watch for major grub updates and then backup the efi partition then. But if you want to be sure all the time, then yes you need to back it up also. Not sure if an older efi file would boot an updated grub & kernel due to version differences.

It really is like the MBR, in BIOS did you backup sector 0 or the MBR?

---

### Post by geohei on 2013-03-14
No, but did the operating system have a mean to change/update the MBR during system updates?

---

### Post by geohei on 2013-03-14
I explain ...

I have dual boot. Windows 7 [W7] and Ubuntu 12.10 [U1210]. Both system might change EFI partition. Now, I keep on installing and using both operating systems [OS]. If one OS gets too slow (too much test software installed), I restore an image backup. However I always used to do this for one OS only; either W7 or U1210.

But knowing now that W7 and U1210 update the EFI partition, I need to change my backup strategy due EFI updates either being missed or updated twice. Both situations should be avoided!

I explain (fictive example, all backups for EFI, W7 system and U1210 system partitions):
jan 2013 - fresh install of W7 and U1210 -> backup 1
feb 2013 - new software for W7 -> backup 2
mar 2013 - new software for U1210 -> backup 3

Before creating backup 2, I restore backup 1 (EFI ??? and W7 partition) and install new software for W7. Now ... if I restore EFI partition, I might kill U1210 EFI updates done so far, making U1210 inconsistent. If I don't restore the EFI partition W7 updates might provide updates which are already installed. Same applies for U1210 updates ...

Both situations are definitely creating inconsistencies.

How should I resolve this ... ?!

The only solution I see is to restore image backups for all 3 partitions (full restore), install new software to both OSs at the same time, and then create an image backup for all 3 partitions (full backup).

---

### Post by oldfred on 2013-03-14
I know Windows has BCD and both have other support files in efi partition. But each has separate folders for its boot files.

I do not do image backups, but prefer just to use rsync and if I have a major failure I will just reinstall and try to restore my data.

---

### Post by geohei on 2013-03-15
Gonna have to resolve this by either (1.) putting Ubuntu on a different HDD (= 2 separate EFI partitions for each OS) or (2.) creating backups only after updating W7 and U1210 at the same time.

---

### Post by oldfred on 2013-03-15
You can install to two different drives with different efi partitions.

 Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

