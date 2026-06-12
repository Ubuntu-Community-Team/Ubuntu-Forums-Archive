---
title: "beware UDF file system?"
date: 2007-11-20
forum: General Help
---

### Post by kornelix on 2007-11-20
Following the insructions in the udf-tools package, I tried to configure a DVD+RW with the UDF file system. It sorta worked, sorta. Extremely slow. DVD lamp blinked forever after file move operation was apparently complete. Unable to unmount DVD. Desktop hung dead. Had to power off and reboot. Tried it again with same result.

From looking at the bug reports on sourceforge UDF project, it is clear that this is less than alpha status software and should not even be in the Ubuntu repositories. The instructions in the package give no warning about this.

---

### Post by malfist on 2007-11-20
The bleeding edge cuts. I use JFS, it's nice and stable and is better, faster, and doesn't cost (CPU wise) better than ext2/3. Although raiser2 and XFS are both really good, I chose JFS because it excels with smaller files and uses a lot less CPU. I forget the site I used for sources but it's on google, just google something like best linux files sytem or whatnot.

---

### Post by Irihapeti on 2007-11-20
I'm inclined to agree. I tried to backup 2 GB of data - took at least 7 hours!! I've no idea how long the disk took to sort itself out after the last file was transferred, because I got fed up and went to bed. The disk seemed to be usable afterwards, but the whole thing is just far too slow. I had no idea it was going to be like that - as the OP says, no warning.

---

