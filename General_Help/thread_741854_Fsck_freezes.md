---
title: "Fsck freezes"
date: 2008-04-01
forum: General Help
---

### Post by SamuliL on 2008-04-01
Hey,

I've had this problem with fsck as long as I can remember when using Gutsy. At first, whenever fsck ran at startup it "merely" messed up my system so that I usually either had to reinstall or fiddle with configuration files (the outcome usually was that after a few hours my Kubuntu was back in business). The fsck appeared at startup maybe once a month for me so I could live with this annoying feature until it got worse: it just froze when checking my /home partition.

The freezing usually took place at 22.x%, but sometimes it got further to something like 30%. After some serious googling I found this thread:
[http://ubuntuforums.org/showthread.php?t=422307]("http://ubuntuforums.org/showthread.php?t=422307")
and booted with the live cd. The live cd also crashes when running fsck on /dev/sdb3 so I just disabled fsck on startup. Since the live cd crashes I have reason to believe my HD is damaged (although this never occured in Feisty). Is there any way to confirm this? I'd guess it's somewhat vital in the long run to get this fixed, any ideas?

Thanks in advance!

---

### Post by justleen on 2008-04-01
by reading your post, i come the same conclusion: something is wrong with the disk.

Most suppliers have seperate disk tools, that will actually check the integrety of the disk it self. I'd suggest you try one of those (from your manufacturer).

Is you /home a seperate partition?
if so, i might be worthwhile to backu the date, delete the partition, re-add it, format as ext3, and run fsck again?

---

### Post by dcstar on 2008-04-01
> **SamuliL said:**
> Hey,

I've had this problem with fsck as long as I can remember when using Gutsy. At first, whenever fsck ran at startup it "merely" messed up my system so that I usually either had to reinstall or fiddle with configuration files (the outcome usually was that after a few hours my Kubuntu was back in business). The fsck appeared at startup maybe once a month for me so I could live with this annoying feature until it got worse: it just froze when checking my /home partition.

The freezing usually took place at 22.x%, but sometimes it got further to something like 30%. After some serious googling I found this thread:
[http://ubuntuforums.org/showthread.php?t=422307]("http://ubuntuforums.org/showthread.php?t=422307")
and booted with the live cd. The live cd also crashes when running fsck on /dev/sdb3 so I just disabled fsck on startup. Since the live cd crashes I have reason to believe my HD is damaged (although this never occured in Feisty). Is there any way to confirm this? I'd guess it's somewhat vital in the long run to get this fixed, any ideas?

Thanks in advance!

Install the** smartmontools** package, enable SMART in your BIOS and run tests on the drive.

---

### Post by SamuliL on 2008-04-03
Ok thanks for your replies!

Fixing this seems relatively large procedure, so I think I'll pass it until 8.10 comes out and do all the configuring at the same time. I'll probably be back for more help then :) 

Anyways, thanks again!

---

