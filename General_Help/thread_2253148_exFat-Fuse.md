---
title: "exFat-Fuse"
date: 2014-11-17
forum: General Help
---

### Post by findingthebalance on 2014-11-17
Have been unable to upgrade to 14.10 because exfat-fuse needed to read and write to an exfat drive is broken. I read a bug report that stated that there is a fix, but it will not be implemented till the nest release. The ability to read and write to an exfat drive has worked fine in previous releases why take so long to issue the fix? I like to use the most recent version of Ubuntu, but this time I can not.

Thank you

---

### Post by mc4man on 2014-11-17
Which bug report?
Here in 14.04 exfat volumes can be read & written to,  are you saying it's broken in 14.10?

---

### Post by findingthebalance on 2014-11-18
Yes it is broken in 14.10. Bug report was confirmed with enough users reporting it.

I had to reinstall 14.04 because I need Exfat support.

"This is a known bug of util-linux (libblkid1) that has already been fixed upstream but not in Ubuntu yet."

---

### Post by mc4man on 2014-11-18
Fixed in 15.04 (vivid) util-linux source - currently 2.25.2-2ubuntu2, actually  fixed with [2.25.2-1]("https://launchpad.net/ubuntu/+source/util-linux/2.25.2-2ubuntu1")source

Edit: while I don't have 14.10 you may be able to use this package for 15.04 in 14.10
[http://packages.ubuntu.com/vivid/libblkid1](http://packages.ubuntu.com/vivid/libblkid1)

---

