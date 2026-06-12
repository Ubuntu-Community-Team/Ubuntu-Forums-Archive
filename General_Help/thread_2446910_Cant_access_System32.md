---
title: "Cant access System32"
date: 2020-07-09
forum: General Help
---

### Post by lenaloyd on 2020-07-09
So, I'm pretty new to Linux, correct me if I get anything wrong. I'm using a live version of Ubuntu booted from a USB drive on a computer that I normally run Windows 10 from. I mounted my Windows partition and tried to open the System32 file, but was faced with a 'this location could not be displayed' message, saying it had encountered trouble while getting information for a file named 'bthci.dll'. It specifies that it's an input/output error but I can't discern what could be wrong. Any help would be greatly appreciated.


Thanks in advance.

---

### Post by wildmanne39 on 2020-07-09
Hello and welcome to the forum, input/output error usually means there is a hard drive issue, you do not want to open System32 files from Ubuntu it will cause corruption/very serious issues.

---

### Post by guiverc on 2020-07-09
I agree with wildmanne39 in I/O errors from your description are usually hardware related. I would stop trying to access the data, and instead query the electronics of the drive (hdd/ssd) to check on it's health, ie. use the SMART built into the drive electronics.

I'll provide [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools).

 The health can be read from CLI (if using a server release; you didn't specify) or via GUI tools such as `gparted` or `gnome-disks` too. They read the data from the drive chips thus won't impact the media at all, then you can plan the best approach for fixing or replacing the problem based on what you find.

---

