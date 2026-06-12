---
title: "My PC wont load GRUB after I installed Ubuntu alongside WIN10"
date: 2021-01-17
forum: General Help
---

### Post by hayloiuy on 2021-01-17
[COLOR=#212121][FONT=Arial]I installed Ubuntu along side Win10. I was informed that there should be a grub menu that lets me choose which OS i want to load. But now it straight up loads Ubuntu. I provided an attachment of my partition. Sda1 and sda2 are my Win10 partitions. The whole of sda4 is Ubuntu. Is there something wrong here? Was the MBR overwritten by Ubuntu?

[/FONT][/COLOR][ATTACH=CONFIG]287759[/ATTACH]
[COLOR=#212121][FONT=Arial]The BIOS boot option is as below. There is an entry for Ubuntu but no Windows. Is this normal?
[/FONT][/COLOR][ATTACH=CONFIG]287760[/ATTACH]

Thanks in advance.

---

### Post by jeremy31 on 2021-01-17
You installed Ubuntu in UEFI mode when Windows was installed in Legacy/BIOS mode

---

### Post by hayloiuy on 2021-01-17
Is this an issue? And is there a way to recover from this?

---

### Post by oldfred on 2021-01-17
BIOS never shows a name, just a drive, so if you boot from the drive Windows is installed on, does Windows boot?

I thought until recently you could not even have Windows in BIOS mode & Ubuntu in UEFI mode on same drive. But a user posted that it did work.
Its just that UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch. Or grub can only boot other systems in same boot mode.

Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since 2012. 
So typically better to have Windows in UEFI mode if hardware is UEFI.

---

### Post by hayloiuy on 2021-01-17
This means i just need to change WIN10 from BIOS to UEFI and GRUB will load? What tools can be used to achieve this?

---

### Post by oldfred on 2021-01-17
You cannot just change Windows from BIOS to UEFI.
Windows requires MBR partitioning with BIOS and requires gpt partitioning with UEFI.
Conversion from MBR to gpt normally erases a drive. There are conversion tools, but best for data only drives.
And has major differences in required partitions.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Backup of your data & reinstall is about the only good option.
How you boot install media, UEFI or BIOS is then how it installs for both Ubuntu & Windows.

---

