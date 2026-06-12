---
title: "Problems moving Ubuntu to new partition"
date: 2017-03-02
forum: General Help
---

### Post by gearheadgeek2 on 2017-03-02
For reasons that are not important here, I have several partitions with different versions of different OSs installed (or rather try to install).  Ubuntu hangs up in the grub update phase repeatedly for any of Ubuntu 10, 12, 14, or 16.  I have found that if I plug in a single drive, Ubuntu installs just fine, but when I try to move that install from that drive to a partition on another drive, it is broken.  It seems to forget at least some of it's configuration.  e.g., it now wants me to log in as guest, the second monitor does not work and resolution is wrong on the only one that does work. While I can fix several of the problems, I can't fix the login issues.  Why is this happening?  How do I stop it?

EDIT:
It appears that I am wrong - it is the recommended update/upgrade that breaks the install.  The questions remains - how do I stop this and/or fix it?

---

### Post by Bucky Ball on 2017-03-02
1. You can delete '10' (presume you mean 10.04 LTS?). No longer supported. 12.04 LTS dies half way through this year. 16.04 LTS good start.
2. How are you moving the install?
3. The other installs aren't important here, but you've mentioned them. Which install are you actually wanting to install and use?
4. If the graphics issue is your only issue in the working install, have you posted about fixing that?

You have mentioned four installs and not specified the one you're having the issues with moving, installing or updating/upgrading. :)

---

### Post by gearheadgeek2 on 2017-03-02
As I said, I need these multiple versions.

I have been using tar | tar to copy the install to a different partition.  I have done this for years without problem.

I haven't had time to check yet, but I think this is moot - it is the upgrade/update that is breaking things not the actual moving.

---

