---
title: "BioLinux 7 (12.04) boot problems (Win 7 already installed)"
date: 2014-02-02
forum: General Help
---

### Post by bdbartgmail.com on 2014-02-02
I have dual booted before, but I can't seem to figure this out.

So I have Windows 7 installed on a Lenovo Thinkpad X131e LRF83DH-3367CTR (CPU Intel Celeron 877), I replaced the HDD with SSD 256G PLEXTOR PX-256M5PRO R

I initially partitioned the SSD with 80GB for Windows 7.  After creating a bootable USB with Biolinux 7 (Ubuntu 12.04) I partitioned another 80GB to / logical partition and ext4 for that OS and 2GB for swap. The installation seemed to go well.  But after I restarted I could not get the laptop to boot into Biolinux.  I thought this was a problem in the BIOS, so I changed the UEFI/Legacy Boot to UEFI only, then I got >>Start PXE over IpV4. So I changed that setting back to Both with priority to  Legacy first and Windows 7 still boots without giving me an option to choose OS.  I think my problem is in the BIOS, but can't figure it out.  I am pretty sure the OS installed correctly.

How do I pick which OS to boot?
I tried holding the Shift and ESC key, but that didn't let me select which OS.

Do I need to repair GRUB?

I am running UEFI BIOS Version G8ET93WW (2.53)

---

### Post by bdbartgmail.com on 2014-02-03
OK so after finding the boot OS option. Only windows 7 is listed, not BioLinux.  Should I try to reinstall??

---

