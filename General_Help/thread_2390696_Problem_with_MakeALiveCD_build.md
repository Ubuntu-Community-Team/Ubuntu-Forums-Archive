---
title: "Problem with MakeALiveCD build"
date: 2018-05-01
forum: General Help
---

### Post by David_Partridge on 2018-05-01
I just ran through the instructions at [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall) to build an updated live cd for my system.

I get the following messages when I try to boot the CD:

/init: . : line 261: can't open /scripts/casper
kernel panic - not syncing: Attempted to kill init!

Help!!!

Thanks
David

---

### Post by rsteinmetz70112 on 2018-05-01
Are you trying to make a custom live DVD?
Your error looks like the squashfs is not properly installed.

Any  system should be able to make a live CD from a download an ISO.

If you are trying to make a live DVD of your system you can use CUBIC.
I had very good success with CUBIC, of course you need a running Ubuntu system to run it.

---

### Post by David_Partridge on 2018-05-01
Yes. I'm trying to make a live CD of my running system.   I'll give it another try tomorrow and maybe take a look a Cubic?

David

---

### Post by David_Partridge on 2018-05-01
I tried again from a completely fresh start - still get the same problem :(

Dave

---

### Post by David_Partridge on 2018-05-26
Is no-one looking after Casper?  CUBIC doesn't do what want which is to build a Live CD based on my running system with all the stuff I have installed like iSCSI for remote tape access.

Dave

---

### Post by David_Partridge on 2018-06-03
BUMP! I'm quite frankly rather horrified that no-one from the Casper team has deigned to respond.

David

---

### Post by PaulW2U on 2018-06-03
> **David_Partridge said:**
> I'm quite frankly rather horrified that no-one from the Casper team has deigned to respond.
I doubt any of the relevant developers have even seen your posts. This is a user forum. We're all users here even the forum staff. The best way to report issues to developers is through bug reports giving a full description of your issue(s).

[https://bugs.launchpad.net/ubuntu/+source/casper/+bugs?orderby=-id&start=0](https://bugs.launchpad.net/ubuntu/+source/casper/+bugs?orderby=-id&start=0) is a list of the currently outstanding Casper bugs. Is your issue there? If not you can always create a new bug report. The process of reporting bugs is outlined on the Ubuntu Help Wiki - [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by David_Partridge on 2018-06-03
I did open a question there, and it just languished for 3 months. :(  I'll try again opening as a bug report.

Thanks
David

---

