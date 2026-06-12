---
title: "UEFI, secure boot, live OS"
date: 2013-07-11
forum: General Help
---

### Post by greatsirkain on 2013-07-11
Just been trying to get ubuntu on a HP pavillion G6 laptop (with windows 8 on it) & after disabling secure boot, enabling legacy support, enabling USB/CD boot and moving them to a higher boot priority than the hard drive I'm no further forward, it still wont boot from CD/DVD/USB. I'm wanting to use Ubuntu live but leave the hard drive untouched if possible, any ideas?

---

### Post by carl4926 on 2013-07-11
Have you checked this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by greatsirkain on 2013-07-11
Thanks, I'll look for fastbootIn/quickboot/faststartup...And make some new Ubuntu disks, I was using the 32bit ones I already had made.

---

### Post by oldfred on 2013-07-11
Only the 64 bit version includes the UEFI capability with or without secure boot on.
Better to use flash drive than DVD as it is a bit faster.

I think these also did the install, but may discuss some of the other issues.
 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by greatsirkain on 2013-07-12
The guy took it back after I did a factory reset, I give it a week before windows 8 is going so slow he can't use it again. I never did get it to boot with any other OS after 4 days of tinkering. Hope next time he says thanks with whiskey instead of rum. I think UEFI is overkill for personal computers and windows 8 is just wrong, like a quasimodo-esque ipad without the good heart underneath it all, but I will be reading through all the links...Know your enemy. 
Never had a problem like that on the other windows 8 machine I cleaned and put Ubuntu on. Nevermind.
Thanks for the help.

---

### Post by grahammechanical on 2013-07-12
You might also want to read about the F6 boot options that we sometimes have to use to get a live session loading.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

