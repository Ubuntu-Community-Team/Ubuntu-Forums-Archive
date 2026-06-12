---
title: "DVD writer can no longer write dvds but can still write cds - any ideas?"
date: 2007-08-05
forum: General Help
---

### Post by ireneshusband on 2007-08-05
A few days ago my dvd writer, which had appeared to be working fine up until then, lost the ability to write dvds. I had just burned 3 dvds without problem, but when I put in the 4th the burn borked half way through. The same happened with the next 2 dvds and then it started borking even before it had actually written anything, leaving a blank dvd (the error message is pasted at below). It has been like that ever since. 

The strange thing is that even after it got into this state it was still able to write a cd without complaining. According to the man in the local electronics store this suggests that the laser is fine because (he says) writing a cd is more demanding on the laser than writing a dvd.

The drive is about 3 years old, but it hasn't received heavy use. I have burned less than 100 disks in all that time, although it appears from browsing the web that some users of this drive have found that it did indeed fail on them fairly quickly. Nevertheless the man in the electronics store said he felt that hardware failure was unlikely and that it was more likely that dma had been disabled for some reason, which apparently happens a lot on his windows box whenever the drive gets slowed down by a dirty disk. I'm not sure this whether such a problem could even arise in Linux, but I ran hdparm and it told me that UDMA2 transfer was enabled for the drive.

I asked the man whether he thought that a dirty lens could be causing the problem, but he didn't think it likely so I didn't buy a lens cleaning kit. But if DMA is configured properly, as hdparm claims it is, then it has to be something else. So is the machine toast? Or does the lens need cleaning after all. Or is something else the matter?


The error message (according to growisofs as called by k3b) goes like:

```
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    1245184/4647725056 ( 0.0%) @0.0x, remaining 435:20 RBU 100.0% UBU   2.6%
    1245184/4647725056 ( 0.0%) @0.0x, remaining 621:55 RBU 100.0% UBU 100.0%
    1245184/4647725056 ( 0.0%) @0.0x, remaining 870:41 RBU 100.0% UBU 100.0%
    1245184/4647725056 ( 0.0%) @0.0x, remaining 1057:16 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=260h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

```

According to [here]("http://pcburn.com/article.php?sid=2127") the error code 0x3 0x0c  0x00 simply means "write error", but the meaning of 0x3 0xa0 0x80 isn't listed.

---

### Post by be4truth on 2007-08-05
My story was similar. First I noticed occasionally DVD write errors after appr. 2.5 years old device. 
I went to Windows XP and confirmed - same results. Sometimes it would work, sometimes it didn't.
Then more and more people complained about readability of my DVDs.
Last step was that I could read less and less DVDs myself.
I tried the drive on different machines with different OS. Same results. Got a new one - all problems solved. They are now so cheap one can't really expect them to last long. The good old computer age changes into a cheap short term concept which, given the rapid progress, might be the right way to go.

---

### Post by ireneshusband on 2007-08-05
> **be4truth said:**
> My story was similar. First I noticed occasionally DVD write errors after appr. 2.5 years old device. .

I suspect you're probably right and that the hardware has simply worn out. Still, I find it strange that the problem came on so suddenly and also that I can still write cds. I'll probably get an optical drive cleaner after the long weekend (It's BC Day here tomorrow, when British Columbians celebrate the wonder of living in a place with trees and mountains and salmon and trees and trees and a really huge number of trees). You never know.

---

### Post by be4truth on 2007-08-06
I was as surprised as you now and refused to believe in a hardware failure. It took me almost a month to admit to myself that I have to get a new one.

---

