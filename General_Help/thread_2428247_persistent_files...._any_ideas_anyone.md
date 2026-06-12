---
title: "persistent files.... any ideas anyone?"
date: 2019-10-01
forum: General Help
---

### Post by alexukalex on 2019-10-01
OK a bit of an odd one this... I have been using Ubuntu for ages (love it by the way) but I'll admit I'm a distro hopper for reasons of curiosity and learning only.
I used ubuntu, then using gparted wiped my harddrive and installed Manjaro... played for a bit, then wiped my harddrive and tried EndeavourOS.... wiped drive then tried Fedora... then wiped drive and installed Ubuntu (wipe drive - delete all partitions, create new device partition table etc etc).
On installing Ubuntu again - I opened my trash bin (recycling bin..) and there were files in there that I remember deleting from Ubuntu prior to installing the other distros....
Can anyone suggest how these persistent files may have remained in the bin?
(i'll resist using a confused emojji.........)

---

### Post by TheFu on 2019-10-01
Because you didn't actually delete the data or reformat the partition?

---

### Post by SeijiSensei on 2019-10-02
Do you have a separate partition for /home? Your trash directory is stored there.

---

### Post by alexukalex on 2019-10-02
Thanks for the replies... but no ,each time I delete all partitions, select the device and create a new partition table... let the distro select the partition scheme automatically (this usually ends up with no separate /home) and then install. The drive is an ssd.

---

### Post by TheFu on 2019-10-02
> **alexukalex said:**
> Thanks for the replies... but no ,each time I delete all partitions, select the device and create a new partition table... let the distro select the partition scheme automatically (this usually ends up with no separate /home) and then install. The drive is an ssd.

I don't think the installer actually reformats the partitions if they don't change.  It has been a few years since I saw a similar issue, but in the end, the fix was using dd to write 4K of /dev/zero to the start of the disk.

---

### Post by Skaperen on 2019-10-02
when i want to wipe the whole drive i wipe the start of each partition and then wipe the start of the drive with 1MB of binary zeros.  in extreme cases i spend a few hours writing TBs of binary zeros.

what may have happened in your case is:  your first install of ubuntu used partitions located away from the start of the drive because another system appeared to already exist, the other distros did not use, or did not format the ubuntu partition, and ... the 2nd install of ubuntu ended up using the same location for the same mount point and did not format it (maybe because mounting it was successful).

can you show us (in code tags) the output of this command:  [COLOR=#0000cd][FONT=courier new]**cat /proc/partitions**[/FONT][/COLOR]

---

### Post by alexukalex on 2019-10-03
Thank you both youve hit the nail on the head... very interesting that deleting partitions and allocating a new partition table doesnt necessarily obliterate the data... thanks Skaperen for the pointer.... i'm off to read the wiki that describes all the different linux partitions etc...... learning all the time!

---

