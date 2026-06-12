---
title: "BackInTime is segfaulting"
date: 2017-07-17
forum: General Help
---

### Post by RobTheBold on 2017-07-17
Like the title says, BackInTime is now segfaulting on my Kubuntu 16.04 system. When run in terminal, nothing but: 
```
[FONT=monospace][COLOR=#000000]Segmentation fault (core dumped)[/COLOR]

[/FONT]
```
appears.

Previously, it had worked just fine. I try to back up at least once per month -- it's been 5 weeks since my last confess^B^B^B^B^B^B^B backup. Last time, all was well, this time I get a segfault. I can't find any recent similar issues when searching the googles. It doesn't seem to matter if I've mounted the backup drive or not before invoking BackInTime -- I've tried it both ways.

Any ideas or suggestions?

Thanks!

Edit: BTW, even running "backintime --version" in terminal give a segfault. It's version 1.1.12-1 in case that matters.

---

### Post by RobTheBold on 2017-07-25
Replying to myself. Looks like maybe I'm the only Ubuntu user running BackInTime, so this post is so I don't forget this stuff later.

Version of BackInTime in the repos (1.1.12-1) was broken by library changes. To get it working again, the testing version 1.2.0~alpha16 needs to be installed from the bit-team PPA. See [https://github.com/bit-team/backintime#install](https://github.com/bit-team/backintime#install)

---

### Post by maglin2 on 2017-07-25
I'm using backintime 1.1.12 on Ubuntu 16.04 , so far (ie today's backup) without problem. Perhaps it's a KDE issue.
Glad you've got it sorted. 
More important to back-up than to be fussy about which tool you use for it!

---

### Post by swissz on 2017-08-16
I have the same issue since the last ubuntu update, with the difference, that for me the CLI interface is still working, so I can start backups from there.

---

### Post by wildmanne39 on 2017-08-16
@ swissz, It would be best to start your own thread so you will have a better opportunity to get the support you need.

Thanks

---

