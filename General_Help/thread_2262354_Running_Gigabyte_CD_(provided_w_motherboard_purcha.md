---
title: "Running Gigabyte CD (provided w/ motherboard purchase)"
date: 2015-01-24
forum: General Help
---

### Post by ozark_hillbilly on 2015-01-24
I have attempted to run the CD that came with my Gigabyte motherboard purchase. After invoking 'run.exe' on the CD with Wine the Gigabyte screen appears and the verbage "Now Loading. Please Wait." appears. There is an onscreen CD icon that is rotating and it appears the program is being loaded. But nothing else occurs.
Do I need to configure something in the Wine Windows Program Loader to make this work or is something else needed? 

Attached is a screenshot of the Gigabyte CD files,etc. One of the screenshots shows a Security Warning and asks if I want to install some needed software, The install fails. The security warning does not always appear with each invocation.


I have been told in the Wine-HQ forum that "Windows hardware drivers don't work in Wine." 
[https://forum.winehq.org/viewtopic.php?f=8&t=24111](https://forum.winehq.org/viewtopic.php?f=8&t=24111)

Do I have any alternatives?

Ed

---

### Post by oldfred on 2015-01-24
You do not need to run that CD. Those are Windows drivers that will not work with Linux anyway.

       Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by Nutria on 2015-01-24
> **ozark_hillbilly said:**
> I have attempted to run the CD that came with my Gigabyte motherboard purchase. 

For what purpose?  If to get the drivers, then -- as others have mentioned -- no need: they already come either in Ubuntu or the Linux kernel (though you may have to upgrade to 14.10 if you have bleeding edge h/w).

---

### Post by ozark_hillbilly on 2015-01-24
I thought there was other programs besides the Windows drivers on the CD.

---

### Post by Nutria on 2015-01-24
> **ozark_hillbilly said:**
> I thought there was other programs besides the Windows drivers on the CD.

:)

There are, but all are Windows programs which touch the h/w in some deep and specific manner which Wine will never consider figuring out how to pass to the Linux kernel.

---

