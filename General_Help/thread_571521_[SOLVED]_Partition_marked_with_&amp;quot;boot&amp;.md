---
title: "[SOLVED] Partition marked with &amp;quot;boot&amp;quot; flag"
date: 2007-10-09
forum: General Help
---

### Post by nvteighen on 2007-10-09
Hi, I've noticed that my Windows partition (NTFS) has a "boot" flag, what does it mean? I'm thinking in removing Windows (I just don't use it anymore for months! :D) and transform that partition into my /home, so I'm curious if I need to know and/or do something else because of this detail.

And also, a question: if bootloaders are located at MBR, outside of any partition, what the hell is that "boot" flag for?

Thanks!

---

### Post by dabl on 2007-10-09
It would only be required by Windows:

[http://support.microsoft.com/kb/114841](http://support.microsoft.com/kb/114841)

HOWEVER, it appears that some of the new BIOS's are using it to determine the boot device, which means Linux (which takes its hdd cues from BIOS) then depends on BIOS finding it. :)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115633](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115633)

---

### Post by nvteighen on 2007-10-11
> **dabl said:**
> It would only be required by Windows:

[http://support.microsoft.com/kb/114841](http://support.microsoft.com/kb/114841)

HOWEVER, it appears that some of the new BIOS's are using it to determine the boot device, which means Linux (which takes its hdd cues from BIOS) then depends on BIOS finding it. :)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115633](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115633)

Thanks! As my Ubuntu partition boots without flag, I assume I don't need to care about it.

---

