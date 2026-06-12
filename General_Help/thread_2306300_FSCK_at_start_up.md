---
title: "FSCK at start up"
date: 2015-12-14
forum: General Help
---

### Post by typos1 on 2015-12-14
I get this message before the OS boots :

[fsck from util-linux 2.26.2
/dev/sda1: clean, 208604/9560064 files,1970577/3822080]

(there are a few numbers missing at the end, but you get the idea, I m guessing there are some problems with the disc, but what and how to fix, after it boots all seems ok.

---

### Post by Dennis N on 2015-12-14
> **typos1 said:**
> I get this message before the OS boots :

[fsck from util-linux 2.26.2
/dev/sda1: clean, 208604/9560064 files,1970577/3822080]

(there are a few numbers missing at the end, but you get the idea, I m guessing there are some problems with the disc, but what and how to fix, after it boots all seems ok.

Nothing wrong here. 'clean' is good. I think the following explanation is still correct:

> All filesystems are checked at boot. If the system was shut down cleanly, they will be marked 'clean', which short-circuits the checking process. Any filesystem that was not found 'clean' will be checked. journaled filesystems will usually be checked quickly due to the journal. ext2 filesystems will be checked completely, which can be time consuming.

source: [http://fog.ccsf.cc.ca.us/~gboyd/cs260a/online/filesystems/checking_filesystems.html](http://fog.ccsf.cc.ca.us/~gboyd/cs260a/online/filesystems/checking_filesystems.html)

The message itself may not always be seen.

---

### Post by SeijiSensei on 2015-12-14
Make sure you always shut down your system from the menus.  If you turn off the power instead, the disk will be checked for errors at the next startup.

---

### Post by typos1 on 2015-12-14
> **Dennis N said:**
> Nothing wrong here. 'clean' is good. I think the following explanation is still correct:


source: [http://fog.ccsf.cc.ca.us/~gboyd/cs260a/online/filesystems/checking_filesystems.html](http://fog.ccsf.cc.ca.us/~gboyd/cs260a/online/filesystems/checking_filesystems.html)

The message itself may not always be seen.

Ah, ok, its on my old pc and I ve just wiped my hard drive and installed Xubuntu, was going to sell it and thought it signified a problem. Thaks, nothing to worry about then.

> **SeijiSensei said:**
> Make sure you always shut down your system from the menus.  If you turn off the power instead, the disk will be checked for errors at the next startup.

I always do ! Its a fresh install.

---

