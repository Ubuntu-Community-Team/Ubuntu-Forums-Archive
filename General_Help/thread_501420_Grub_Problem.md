---
title: "Grub Problem"
date: 2007-07-15
forum: General Help
---

### Post by knofls on 2007-07-15
I am getting really desperate ....

I had Ubuntu on a partition of my notebook - during formatting the partition it crashed - afterwards when tried starting again there was just a grub error message - i couldn't do anything (F2, or F8 didn't work) - i formatted the whole drive (deleted all the partitions too) but the progrm is still there and there is the same error message ...

would be great if someone knows how to fix that :(

/edit: oh yeah - fixmbr and such won't work - and the next problem is - i don't have a cd i could boot of since it is all in  a partition provided by sony ... (what i can't access since the notebook won't start)

---

### Post by mikewhatever on 2007-07-15
If you also still have Windows there, use the Super Grub CD to fix the MBR.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Why were you formatting the Ubuntu partition?
If you have formatted the whole drive and deleted all of its partitions, you should be looking for an OS to install there instead of fixing GRUB errors, since in that case, the sony partition is gone too.

---

### Post by knofls on 2007-07-15
thx - the saved the sony partition to an external hd before formatting it all ... - the problem is that because of the grub error i am not getting anywhere (not to the recovery menu, not into windows - nothing) - i am just setting up the nb with windows 2k from a friend and hope to access the mbr once the system is set up by booting from the cd.

thx for the links - i ll try that too ...

why i was formatting the ubuntu partition?
i guess because i am stupid ... - should have asked someone before - thought it was as easy to get rid of as installing it :)

---

### Post by mikewhatever on 2007-07-15
For the future, put the Windows boot loader to the MBR with the SGD before you remove Ubuntu. For more ways to do it check here [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

