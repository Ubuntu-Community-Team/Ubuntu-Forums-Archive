---
title: "Is NTFS partition possible on current linux hdd."
date: 2007-02-11
forum: General Help
---

### Post by wyrmwraith on 2007-02-11
and if known can this partition be used for a windows swapfile? I have dual boot windows xp and ubuntu. Wanting to utilise the linux hdd for a windows swapfile (virtual memory) preferably without formatting the drive.

Windows detects the drive in device manager however it isn't read/write accessable naturally. I presume having a ntfs partition would fix this.

---

### Post by dpar on 2007-02-12
I beleive GParted will create an ntfs partition on your linux drive that windows will then see as read/write. I'm not absolutly sure because it has been a while since I used Gparted.

---

### Post by Kenja on 2007-03-02
From what I remember, writing to NTFS is not trustworthy.  How about an ext2 swap file?

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

