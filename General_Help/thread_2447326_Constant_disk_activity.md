---
title: "Constant disk activity"
date: 2020-07-16
forum: General Help
---

### Post by usndmac on 2020-07-16
On Ubuntu 19.10.

I have a sata drive mounted in fstab, using the UUID. The mount point is /bulkstore. 

I noticed the disk activity LED cycling constantly.

nmon shows the disk is being written to repeatedly with a burst of ~5Mb. 

But, there are no files and no program accessing. 

What's going on?

Did I miss some setting in fstab?

---

### Post by yapidumoac on 2020-07-16
[COLOR=#222222][FONT=arial][/FONT][/COLOR]$iotop -o .. disk i/o usage by process or thread

---

### Post by Impavidus on 2020-07-17
Ubuntu 19.10 reaches end of life today. The problem may still exist in 20.04, but I suggest you get that installed anyway.

---

### Post by usndmac on 2020-07-17
I appreciate that and have upgraded other machines to 20.04.

But, this particular PC runs a program that has not fixed the Pyside issue that won't allow it to build in 20.04. So, I'm waiting for that.

And, after reboot this AM, the disk activity isn't happening, so, until it appears again, can't trouble shoot anyway. :(

---

### Post by TheFu on 2020-07-17
I feel your pain about an OS losing support, but not having a viable option to upgrade.

Every week once a release goes EOL, it becomes harder and harder to migrate to the next release.  Repos will disappear.  In a few months, the only answer will be a fresh install of the next release.

Of course, the security aspects for any unpatched OS get worse and worse daily too, so be certain the system isn't on the internet.

---

