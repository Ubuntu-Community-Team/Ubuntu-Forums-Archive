---
title: "CVE Status for Repository Firejail Version"
date: 2019-12-18
forum: General Help
---

### Post by maglin2 on 2019-12-18
I notice that the version of firejail in the 18.04 repositories (0.9.52-2) has two open CVEs against it [https://firejail.wordpress.com/download-2/cve-status/](https://firejail.wordpress.com/download-2/cve-status/)

Anyone have any advice to offer on the significance for a desktop user running browser (chromium) and email client (thunderbird) under firejail 0.9.52-2?

Thanks

---

### Post by Holger_Gehrke on 2019-12-18
CVE-2019-12499 seems to only affect you if you run firejail as root and shut it down by sending it a SIGKILL or using the --shutdown option. 

CVE-2019-12589 needs you to start a new process inside the jail from outside of it by doing 'firejail --join="NAME OF JAIL" NAME_OF_PROGRAM' after a program inside the jail has prepared the way for it by removing the filter rules (this removal won't affect processes already running inside the jail or their child processes, so you need a new process that is not a child of one of the processes inside the jail). 

To me neither seems to be the kind of thing a normal desktop user would do.

Holger

---

### Post by maglin2 on 2019-12-18
Thanks - I'd sort of thought that, but didn't really have much confidence in my ability to draw justifiable valid conclusions from the github discussions.
I guess I was also a bit reassured by the fact that Ubuntu hadn't updated the repository version, but since it's years since the repository version of firejail (with default profiles) has run firefox successfully ootb I wasn't too reassured by that.

---

### Post by TheFu on 2019-12-18
I pulled new profiles down, but still use the repo version of firejail.  Basically, web browsers are constantly changing to improve security while also trying to improve performance, so the constraints for them in firejail sometimes need to be modified.  The new profiles let us get those new constraint profiles or locally edit them if we feel competent to handle that task.  

Wish the snap packages allowed local control. It is one of my largest issues with snaps.

---

### Post by maglin2 on 2019-12-19
I found a fix a year or so ago on the mint forum.
Your post has just made me realise there may be a more official home for these things somewhere
[https://github.com/netblue30/firejail/tree/master/etc-fixes](https://github.com/netblue30/firejail/tree/master/etc-fixes)
Bookmarked!

---

