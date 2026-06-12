---
title: "trouble formatting 1TB thumb drive"
date: 2015-03-27
forum: General Help
---

### Post by Autodave on 2015-03-27
I cannot seem to be able to get this thumdrive formatted and usable.  It came with exFAT on it.  I am trying to get Windows NTFS on it, or even FAT 32.  Last resort would be ext3.  Unfortunaely, I keep coming up with errors no matter what one I try.  I am using gparted to do this.  Any suggestions to what I may be doing worng?

---

### Post by DuckHook on 2015-03-27
Many USB thumb drives have a translation layer on chip, which means that instructions from USB interface are not necessarily the instructions received by the SRAM chip. A 1TB thumb drive is absolutely bleeding edge, so what funny firmware is on the drive is anybody's guess. Gparted may simply be unable to access the underlying guts of the drive itself.

Moreover, FAT32 is completely inadequate for such a massive drive, and NTFS is far too overhead-intensive and risks burning out your thumbdrive. This would be disastrous as I understand 1TB thumbdrives to be over $1K. BTW, this was the reason MS invented exfat. Any drive over 32GB should not be using FAT32.

I format my 64GB ssd cards and thumbdrives to ext2 (because it has no journal and therefore is gentler on write-fatigue), but I don't ever use these cards/drives in Windows, which will not recognize them. You can also download the exfat driver from the repositories:```
sudo apt-get install exfat-fuse exfat-utils
```...the Linux implementation of exfat works in fuse and not system level, but it gets the job done. Once downloaded, refer to man pages for usage details, including formatting instructions.

---

### Post by DuckHook on 2015-03-28
> **DuckHook said:**
> ...1TB thumbdrives to be over $1K......and if you paid anything less than $1200, you have probably been snookered by a fake Chinese product that stamps 1TB on the cover, modifies the firmware to report 1TB, but actually only has 8GB of SRAM inside. For such drives, the problem is that gparted cannot make heads or tails of the drive because it cannot create a partition table or file structure that resolves the discrepancy between the reported size and the actual physical size of the stick.

If you tell gparted to only create a 8GB partition, you can often use these sorts of drives as 8GB drives. However, even if you successfully create a larger partition table, you would just be creating a time bomb. Such a drive will lose any data written to it beyond the physical limits of its 8GB capacity, but it will do so silently and without any complaint. You will just later find no data where you expected something to exist.

Sorry to be the potential bearer of possibly bad news, but this is a known scam.

---

### Post by Autodave on 2015-03-28
That seems to be exactly what's wrong: a scam.  Thanks for the reply!

---

