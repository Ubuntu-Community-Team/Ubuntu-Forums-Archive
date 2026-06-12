---
title: "no block devices found"
date: 2007-11-13
forum: General Help
---

### Post by dcjmack on 2007-11-13
Having run Wubi-7.04.04.exe, I rebooted and selected "Ubuntu" from the boot manager list.

Things looked promising:

```

hd (0,1)
Filesystem type is ntfs, partition type 0x7
Loading, please wait...

```

ooooooh pretty exciting!!!!


but after a while I get...

```

no block devices found

```

I searched for a while before I posted - the word "no" seemed to prevent me from getting any search results.  I have a SCSI RAID 'array' (one hard disc) on a Dell Precision PWS670 (it's my work computer).

Any ideas?

---

### Post by ago on 2007-11-13
Try wubi 7.10 (requires DESKTOP 7.10 ISO)

[http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by dcjmack on 2007-11-14
right. now when I reboot, after watching the ubuntu progress bar bounce back and forth, I get a 'busybox' command console.  

What now?

**[edit]**
Ahh I see from [http://ubuntuforums.org/showpost.php?p=3700143&postcount=7]("http://ubuntuforums.org/showpost.php?p=3700143&postcount=7") that it's not a good thing

I'll try the debug parameter once I've finished work.
**[/edit]**

---

