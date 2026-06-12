---
title: "Pc won't boot into windows 8.1 after deleting ubuntu partition!"
date: 2015-03-22
forum: General Help
---

### Post by mastrocode on 2015-03-22
I recently deleted the partition ubuntu was on because I didn't like the os, but now whenever I try to boot to my regular windows os I get

"error: unknown file system.
Entering rescue mode...
grub rescue>

HELP!

(pease not in new to the whole linux stuff about would be cool if you could guide me through this.

---

### Post by yancek on 2015-03-22
Since you have windows 8.1, you probably are using UEFI/GPT to boot which would mean you have separate boot files on a FAT32 partition for both windows and Ubuntu.  There are a number of possible reasons but to eliminate some of them it would be best if you went to the site below and downloaded and burned the boot repair iso to a CD, boot with it and select the option to Create Bootinfo Summary.  Then post the output here and someone familiar with UEFI/GPT should be able to advise you.  Link to boot repair below:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

