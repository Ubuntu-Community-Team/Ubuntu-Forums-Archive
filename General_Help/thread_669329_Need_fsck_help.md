---
title: "Need fsck help"
date: 2008-01-16
forum: General Help
---

### Post by xunil76 on 2008-01-16
i need some help with a 1.2GB file named "FSCK0000.REC".  i know that it is a file which contains data from a corrupted section (or sections) of the hard drive.  what i need to know is how i can read it to see what files are contained within it, and if the files are something that i would like to recover, how i would go about doing that.

i know basically nothing about the fsck utility and how to use it, but from what i have gathered from searching on here, it is something that is best not used on a mounted drive.

since this file is contained on a completely separate hard drive from my OS, does that mean i can simply unmount that hard drive, then run fsck from within Xubuntu, or will this still require that i reboot into the fsck utility?  and how do i go about doing so?

---

### Post by bodhi.zazen on 2008-01-16
See if this thread is of any help :

[http://www.linuxquestions.org/questions/linux-hardware-18/i-ran-fsck.vfat-to-repair-hard-drive-and-got-a-bunch-of-.rec-files-515691/?](http://www.linuxquestions.org/questions/linux-hardware-18/i-ran-fsck.vfat-to-repair-hard-drive-and-got-a-bunch-of-.rec-files-515691/?)

You may want to look at something like testdisk or photorec : 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
		How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)
	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Last this article giev some clues of what may need to be done to recover the data ;

[http://www.honeynet.org/scans/scan24/sol/bob/answers.html](http://www.honeynet.org/scans/scan24/sol/bob/answers.html)

---

