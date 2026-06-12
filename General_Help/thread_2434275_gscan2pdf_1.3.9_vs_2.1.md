---
title: "gscan2pdf 1.3.9 vs 2.1"
date: 2020-01-03
forum: General Help
---

### Post by wjbmd48 on 2020-01-03
Hi:

I'm running 32-bit  Lubuntu 18.04 on a T420s, works great.

Previously, I had no problems with this setup driving my old Canon 3240 scanner with gscan2pdf, but it doesn't work properly on a new install, same system. (It'll scan just one page, won't save it, then stops.)

Troubleshooting this, I see that my old machines, on which it worked properly, had version of 1.3.9, but the new install has version 2.1.0.

When I tried to install the version 1.3.9 from sourceforge, I'm told there's an unmet dependency, libsane-perl, which I can't install on my new system, which apparently runs on libimage-sane-perl.

Any ideas on how to fix this?

Thanks!!

Bill

---

### Post by wjbmd48 on 2020-01-03
Further parsing this out, it's clearly a problem with gscan2pdf version 2.1.0; none of the systems with it work properly, all the ones with version 1.3.9 do work.

Ideas?

Bill

---

### Post by kurt18947 on 2020-01-03
If I can remember, I'll check what version of gscan2pdf I have when I get home. I have a Brother multifunction, no Canon but I  can get you the version. Does Simple scan work?

---

### Post by wjbmd48 on 2020-01-03
Thanks for the reply!

I downloaded both simpescan and xsaneimage scanner, and both had the same problem.

This problem just appeared, and I'm wondering if it's not a bug relating to the change from the libsane-perl to the libimage-sane-perl dependency?

Bill

---

### Post by mörgæs on 2020-01-04
Lubuntu 18.04 is a dead-end and I expect that you will encounter less problems in a fresh install of Lubuntu 19.10.

Gscan2pdf is version 2.5.7 here, by the way.

---

### Post by wjbmd48 on 2020-01-04
Yup, I installed 2.6.2 last night, same problem.

It's not that big of a deal, I can always use a windows machine for the odd bit of scanning I need.

Could you expand on what you mean by 18.04 being a dead end? It's supported until 2023, and if I'm going to upgrade, I'd rather wait for 20.04, which I assume will be LTS.

Thanks!

Bill

---

### Post by mörgæs on 2020-01-04
It's a dead end because it is built on LXDE (maybe not the main problem here) and because all old software packages are buggy. 

18.04 is supported in the sense that security related bugs are fixed, nothing more. 

[https://ubuntuforums.org/showthread.php?t=2428735&page=2&p=13896604&viewfull=1#post13896604](https://ubuntuforums.org/showthread.php?t=2428735&page=2&p=13896604&viewfull=1#post13896604) (written one release ago).

The length of the support period should be the least of people's concerns.

---

### Post by wjbmd48 on 2020-01-04
OK, got it, thanks for taking the time.

I'm generally happy with 18.04, tho you're right, it is a tad buggy.

I'm in no rush; is there any harm waiting for 20.04?

Bill

---

### Post by mörgæs on 2020-01-04
There is no harm in relation to security. In relation to functionality it's anyone's guess. 

On the other hand there is no point in waiting. Lubuntu 20.04 is going to be a close relative to 19.10, both of which are markedly different from 18.04. If you believe that a clean install of 20.04 is going to solve the problem chances are that the same applies to 19.10.

---

### Post by wjbmd48 on 2020-01-04
OK, got it.

You got me going, I'm installing 19.10 on a spare machine; I don't see the encrypt-on-install option as with previous versions. Is that done after the install?

Bill

---

### Post by mörgæs on 2020-01-04
I haven't used it so I don't know. 
For testing purposes I think it's fine to stick to a standard install.

---

### Post by wjbmd48 on 2020-01-04
OK, thanks for everything.

I'll keep the thread open in case someone has more info about the gscan issue.

Tx,

Bill

---

### Post by mörgæs on 2020-01-04
Yes, please post your findings. 
Begin with using only the packages delivered as part of the standard install. Downloading and installing stuff from outside should not be necessary.

---

### Post by wjbmd48 on 2020-01-04
Yup, I always do.

OK, I see how to do the encrypted install, thanx!

Bill

---

### Post by kurt18947 on 2020-01-04
Okay, running gscan 2.1 here on 18.04 64 bit mainline Ubuntu. I occasionally see one problem that may or may not be related. If I haven't logged out recently and use gscan2pdf 2.1, it will scan fine won't save multiple scanned images. I get an error message relating to python though I don't recall the exact message. If I log out and back in before scanning, the problem doesn't occur. If I have quite a few sheets to scan I scan one or two then save them. If I'm going to have a problem I'd rather have to re-scan a few sheets than re-scanning many sheets. Then do save/replace every so often as I scan more sheets. 

I do have one machine running 19.10 and it seems pretty bug free for normal stuff. I haven't tried scanning with that machine. I generally upgrade LTS to LTS so am waiting for 20.04 to be out a few weeks before upgrading.

---

