---
title: "Unable to mount 320 GB Filesystem"
date: 2015-05-21
forum: General Help
---

### Post by RagnarTheKing on 2015-05-21
Hi, I've been trying to run my HDD in my ubuntu 10.04 and this message come up every time :confused::(  the hdd contain an important files please I need help without format :cry:

**Unable to mount 320 GB Filesystem**
> Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x3: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

and Thanks

---

### Post by mumie_die on 2015-05-21
Hi there,

where does that drive come from? Was it running in a fakeraid?

greets

---

### Post by oldos2er on 2015-05-21
> In the first case run chkdsk /f on Windows then reboot into Windows twice.

Have you tried this?

---

### Post by Mark Phelps on 2015-05-21
Presuming the hard drive came from a Windows PC, we need to know which version of Windows was running on that PC -- as the steps to repair this are not the same for each Windows version.

---

### Post by RagnarTheKing on 2015-05-22
> **oldos2er said:**
> Have you tried this?

I don't, thanks :KS

> **mumie_die said:**
> Hi there,

where does that drive come from? Was it running in a fakeraid?

greets

> **Mark Phelps said:**
> Presuming the hard drive came from a Windows PC, we need to know which version of Windows was running on that PC -- as the steps to repair this are not the same for each Windows version.

It's actually an external hardisk, and I used to use it in w 7 and 8, last time with w 8.
Thanks :KS

---

### Post by dino99 on 2015-05-22
> **RagnarTheKing said:**
> Hi, I've been trying to run my HDD in my ubuntu 10.04 

you should not still use 10.04 now; its fully dead, unsuported and is way to old compared to your other used windows OSs (ntfs-3g has got so many upgrades)

---

### Post by yancek on 2015-05-22
The solution is in your message in the initial post.  You did not properly shut down windows before removing the drive and you need to do that with the drive attached to your windows system.  Not sure if you need to use windows 10.  Someone else more familiar with windows should be able to tell you.  It's generally not a good idea to use beta test software (windows 10) on your primary computer.

---

### Post by RagnarTheKing on 2015-05-22
> **dino99 said:**
> you should not still use 10.04 now; its fully dead, unsuported and is way to old compared to your other used windows OSs (ntfs-3g has got so many upgrades)

I use ubuntu 10.04 as primary system, if I update it, its gonna work?

> **yancek said:**
> The solution is in your message in the initial post.  You did not properly shut down windows before removing the drive and you need to do that with the drive attached to your windows system.  Not sure if you need to use windows 10.  Someone else more familiar with windows should be able to tell you.  It's generally not a good idea to use beta test software (windows 10) on your primary computer.

so should I go use the hardisk with windows system and safely remove the drive and try to run it here? btw it's doesn't work with windows too :(

:-|

---

### Post by RagnarTheKing on 2015-05-23
please anyone

---

### Post by leunam12 on 2015-05-23
Install Ubuntu 14.04. You are running an unsupported OS that is too old. What brand is this HDD? Go to the manufacturer's website and see if they have a live CD diagnostic/repair utility that will help you with this; since it's not working in Windows I'm assuming that you couldn't run chkdsk /f

---

### Post by Vladlenin5000 on 2015-05-23
> **RagnarTheKing said:**
> 
so should I go use the hardisk with windows system and safely remove the drive and try to run it here? btw it's doesn't work with windows too :(

:-|

Yes, that would be the preferred method, the 'best practice' in "US terminology" ;)
What "doesn't work" exactly? Can you see your drive in the file explorer (Windows Explorer??) but can't access its contents? Or isn't it visible at all (in explorer)?
The troubleshooting must be done accordingly. This are very different scenarios...

---

