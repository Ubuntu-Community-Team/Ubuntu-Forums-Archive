---
title: "Vista on C:, Wubi on E:...possible?"
date: 2007-10-26
forum: General Help
---

### Post by Croathlete on 2007-10-26
I have Vista installed on my C: drive and attempted to install Wubi 7.10(I think rev 376) onto my second drive which is E:.  It installed and rebooted, but did not give me an option to boot into Ubuntu.

I downloaded EasyBCD and did not see an entry that should have been created by Wubi.  I attempted to create one with EasyBCD, but that just loads into GRUB and that's as far as I get.  I'm assuming it's looking for something on C:, but that's as far as my "expertise" takes me.

Any suggestions? :confused:

---

### Post by ago on 2007-10-26
What version of wubi did you use? Latest is rev377.

You have to point the bootloader entry to wubildr.mbr, which should be in ubuntu/winboot, but that should be done for you automatically.

You have to uninstall any previous version though

---

### Post by Croathlete on 2007-10-26
Thanks for the quick reply.  I'll try that again with the new version tonight.

In case it doesn't do that automatically, how would I point the bootloader to wubildr.mbr?  For the few minutes I was fiddling with EasyBCD, it didn't seem like it gave the option to specify a partition, let alone a path when adding a Wubi entry.

---

### Post by ago on 2007-10-26
You can use the commandline as well, there are a few guides for that, but hopefully wubi should take care of it. Make sure that old versions are uninstalled, and maybe run chkdsk /r

---

### Post by rohedin on 2007-10-28
Just to say, it works fine on seperate drives on 7.04.

---

