---
title: "Raid 5 Setup Not Working"
date: 2008-01-16
forum: General Help
---

### Post by christo16 on 2008-01-16
Hello,
I've setup a RAID 5 4 x 500 GB drives using my onboard raid card, its a nforce 570 series.  The BIOS recognizes that the raid is setup but as soon as i boot into ubuntu (7.04) it doesn't recognize the raid, it just sees 4 empty drives.  Am I missing something here, do I need drivers for ubuntu from nvidia?
Thanks!

---

### Post by rogblake on 2008-01-16
What you have there is "fakeraid" -- it is not a real hardware RAID controller, it is software RAID with a BIOS setup program. Chances are that Nvidia only provides a Windoze driver.

You'll need to either purchase a Linux-compatible RAID card (like 3Ware) or use Linux's own software RAID.

---

### Post by fjgaude on 2008-01-16
You can use dmraid to access the raid... some have had succes doing this. This HOW-TO might help:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Let us know how you do.

---

