---
title: "Slow boot dual Win 8 Ubuntu 15.04"
date: 2015-04-30
forum: General Help
---

### Post by avents on 2015-04-30
My dual-boot laptop has been slow to  boot (both Win and Ubuntu 15.04) and I tried to use Boot REpair to see if that helps.

Here are errors and I don't understand .
" The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
An error occurred during the repair.
Please write on a paper the following URL: [http://paste.ubuntu.com/10952358/](http://paste.ubuntu.com/10952358/)
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file! "

Additionally, Boot Repair said that Win partition is almost full (/sda4 ) and I tried to extend it using Gparted but it did not work. I seldom use Windows but keep updating it and it grew over the years.
Actually, both Win and Ubuntu do end up booting but slower than before.
I will be away from the machine but should try to answer any questions when I return later on.
Thanks

---

### Post by oldfred on 2015-04-30
If an UEFI system and you have Ubuntu in CSM/BIOS/Legacy boot mode then it has to boot in UEFI mode to Windows and then reboot using one time UEFI reboot option into legacy mode. So that slows boot.

Also any Windows NTFS partition that is less than 30% free space starts to slow down. At 10% free it gets extremely slow and you may not really be able to run a defrag as there is so little working room, or it will take days. Then time to houseclean Windows.

---

