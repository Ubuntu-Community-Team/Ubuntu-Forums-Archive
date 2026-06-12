---
title: "Did I change the sata driver correctly?"
date: 2007-01-30
forum: General Help
---

### Post by rev_b on 2007-01-30
I have a motherboard with ULI chipset M1695; I have a 160Gb SATA disk with 2 partitions (formated with NTFS for WinXp) and a 120gb IDE one. I installed Ubuntu on the IDE disk and works just fine, but I noticed some random freezes if the Sata NTFS partitions are mounted, when accessing them.

I really don't need the info on the Windows partitions, I have my documents backed up in a Linux ext3 one, and I acess them from there.

But I decided to give it another try and I tried to replace the driver with the one ULI smartly offers for linux kernel 2.6.x; however, there are no installers for Ubuntu or Debian. Only for Fedora, Redhat and Suse. I found however a file named sata_uli.ko and I noticed Device Manager is listing the device as ULi 5289 SATA with info.linux.driver sata_uli.

I looked for this file on my system and it's located on /lib/modules/2.6.17-10-generic/kernel/drivers/scsi . They have diferent sizes, so it's not the same. I just backed up the old file and replaced it with the sata_uli.ko from ULI driver package. I rebooted and all is fine; I already mounted the SATA disk and it seems to be working fine (soon to tell).

So can I assume my system is using the binary driver from ULi?

---

### Post by rev_b on 2007-01-30
Or would it be necessary to compile the kernel or something like that?

Maybe I shoud have posted it on absolute beginner...

---

