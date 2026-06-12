---
title: "HP Pavilion DV5269 ea unsuccesful installation of Edgy Eft"
date: 2006-12-09
forum: General Help
---

### Post by mikewhatever on 2006-12-09
Hi everyone,

I need advice on Edgy installation on HP Pavilion DV5269ea. If more specifications are required, please see here:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00777995&lc=en&cc=us&dlc=en&product=3279914&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00777995&lc=en&cc=us&dlc=en&product=3279914&lang=en)

I could not install Edgy at all. Got stopped at partitioning stage, resizing ntfs partition.

I used ubuntu-6.10-alternate-i386.iso downloaded over bittorrent and md5sum checked, and followed the instructions from here:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
but could not get beyond resizing ntfs partition of 70 GB.
At fig 13 in the site just mentioned, I type the new partition size (70% or 50 GB), the screen turns blue, the HD light turns on for a few seconds, and then it is back to fig 11 with the same size partitions. There is 40 GB of free space on ntfs partition and I've defragmented before the install.

Don't know if this is relevant, but there is a FAT32 recovery partition of about 9 GB and another 1.2 GB ntfs partition of unknown functionality. This last one dosn't show in Windows under My Computer, but only when partitioning with ubuntu CD.

Well,that's about it,

any ideas?

---

### Post by mikewhatever on 2006-12-09
It looks like this forum is a very busy place. It is probably due to the growing popularity of Ubuntu. The more people try it, the more problems arise. Perhaps forums are not the place to solve them, what do you think?

---

### Post by mikewhatever on 2006-12-11
OK, no HP experts so far. :(  I've been looking around and guessing. One guess is, there is a Recguard.exe process, protecting the deletions of the recovery partition by accident. Could it be relevant? I was not trying to delete the recovery partition, but still... 
Any kind of advice would be appreciated.

---

### Post by mikewhatever on 2006-12-17
It is somewhat discouraging to be the only poster in the thread, but I will just assume that the problem I ran into is either rare or yet unknown. I was able to repartition and install Edgy Eft today. The clue to the nature of the problem is posted here:
[http://ubuntuforums.org/showthread.php?t=290850](http://ubuntuforums.org/showthread.php?t=290850)

](*,)

---

