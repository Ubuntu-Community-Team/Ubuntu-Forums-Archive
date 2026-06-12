---
title: "External USB Hard Drive &quot;Cannot eject volume&quot; ERROR"
date: 2007-08-20
forum: General Help
---

### Post by joeinazyes on 2007-08-20
I'm running Feisty 7.04 and have two USB external hard drives.  Each is FAT32 500GB and 400GB.  BOTH will not shut down properly when I right click and choose "Eject".  BOTH drives show ERROR windows claiming "Cannot eject volume".  The mount point info is as follows:

Mount Point:  /media/disk
File System:  vfat
Mount Options:  rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cdp437 iocharset=iso8859-1 shortname=mixed utf8
UUID:  4583-193C

P.S. I specifically want read and write permission on these drives when they fire up.  However, they refuse to "Eject".

Please advise.

---

### Post by joeinazyes on 2007-08-20
Fixed it myself, thanks to this post:

[http://ubuntuforums.org/showthread.php?p=2474560#post2474560](http://ubuntuforums.org/showthread.php?p=2474560#post2474560)

This was never broken in Edgy, Dapper, Breezy.  Why is this broken now with Feisty?!

---

