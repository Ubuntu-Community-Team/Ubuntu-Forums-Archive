---
title: "No LibreOffice Draw in Xenial?"
date: 2016-09-02
forum: General Help
---

### Post by texpat on 2016-09-02
Hi,

I upgraded from Trusty to Xenial a few days ago and now I seem not to have LibreOffice Draw installed (I did have it installed in Trusty). I try to install it from the Software Center but that gives me the following error message:

```
The following packages have unmet dependencies:

libreoffice-draw: Depends: libreoffice-core (= 1:5.1.4-0ubuntu1) but 1:5.1.5~rc2-0ubuntu1~trusty1 is to be installed
```

Any ideas? I really would like to have Draw...

Thanks for reading, and appreciate any help.
Tx

---

### Post by ubu_dynamite on 2016-09-02
Try removing or downgrade libreoffice-core make sure non of your sources point still to trusty in your sources.list update your sources and reinstall.
Looks like trusty version of libreoffice-core is newer then xenial.

---

### Post by ian-weisser on 2016-09-02
Look at the version numbers: 

1:5.1.4-0ubuntu1   (provided by Xenial-security)
1:5.1.5~rc2-0ubuntu1~trusty1  (provided by some non-Ubuntu source)

The problem: You have introduced a *version conflict*.  The older package has the higher version number. Version numbers matter in Debian/Ubuntu.
Apt is assuming that version 5.1.5 is preferable to version 5.1.4...but your entire system is designed to be compatible with 5.1.4.

Back when you used Trusty, you seem to have added some non-Ubuntu packages from a non-Ubuntu source in order to upgrade LibreOffice.
Then, when you release-upgraded to Xenial, apt looked at the new LibreOffice packages, discovered that the existing version was higher, and made no changes.

You might be confused by the problem. You are many thousands of times smarter than poor apt.
You cannot have 5.1.4 and 5.1.5 installed at the same time. They *conflict*. You must resolve the version conflict by telling apt which version you really want.

Here's one way:
1) Uninstall your non-Ubuntu 5.1.5 version of LibreOffice.
2) Disable or delete that non-Ubuntu 5.1.5 source from /etc/apt/
3) Delete all 5.1.5 packages from that source from your package cache in /var/apt/cache/.
4) Refresh your package database based on the new sources (sudo apt update)
5) Install the Ubuntu 5.1.4 version of LibreOffice.

Here's another way:
1) Enable that 5.1.5 non-Ubuntu source for 16.10. Assuming it exists.
2) Install LibreOffice draw from that source.

If you need help following one of these paths, just let us know which path you want to pursue.

This kind of problem is annoying to fix...but is super-easy to prevent. Before doing a release-upgrade, simply uninstall all non-Ubuntu packages.

---

### Post by texpat on 2016-09-02
Oh dear, 

yes, indeed. I'd forgotten that I installed a non-Software Center version. Please accept my apologies for this. And thanks to both for pointing out the problem.

---

