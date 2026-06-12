---
title: "Cannot mount HDD"
date: 2007-12-03
forum: General Help
---

### Post by garrett218 on 2007-12-03
Last night my WindowsXP box tossed up a BSOD saying there was a bad sector on the primary HDD.  When I tried to reboot the machine it failed after BIOS saying it could not find the boot drive.  

Today at work my colleagues and I install Unbuntu 7.10 onto a new SATA HDD in my PC.  After installing this I was able to then mount my second SATA HDD (not the one that failed but my Raptor that I kept only games on) but when I tried to mount the original XP drive to see if I could recover any of the data.  I keep encountering the same error:

Failed to mount '/dev/sdc1':Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important!  If you have SoftRAID/FakeRAID then you must first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details

Does this mean the Windows HDD is toast? Is there anyway to recover the data on it?

alex

---

### Post by merlinus on 2007-12-03
chkdsk:c /f will attempt to repair errors on the hdd.  (change c to whatever letter windows is calling that drive)

More info here:

[http://en.wikipedia.org/wiki/Chkdsk](http://en.wikipedia.org/wiki/Chkdsk)

---

### Post by garrett218 on 2007-12-03
I would try that command but I no longer have a windows box since the HDD containing the Windows OS is the one with the bad sector.  Is there anything I can do from Linux?

---

### Post by geraldm on 2007-12-04
It should be possible to recover from a bad sector on an NTFS using filesystem tools.
I can't provide specific package details because NTFS is not used here.  Perhaps look for
the tools.  ntfsprogs would be one package to check.  There may be others in ubuntu or debian packages that would work.

Gerald

---

