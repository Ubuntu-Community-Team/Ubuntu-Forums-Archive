---
title: "When will 18.04.6 come?"
date: 2021-05-21
forum: General Help
---

### Post by iamacmol on 2021-05-21
Is there a schedule with 18.04.6? 
A bug of glibc makes my program not working. I did some searching, then found glibc [2.27-3ubuntu1.3]("https://launchpad.net/ubuntu/+source/glibc/2.27-3ubuntu1.3") will fix the bug.

But this new glibc is not included in any of 18.04 releases. 
(Newest version of ubuntu18.04 is 18.04.5, it is released at Aug 2020.  and [2.27-3ubuntu1.3]("https://launchpad.net/ubuntu/+source/glibc/2.27-3ubuntu1.3") is released at Sep 2020.)

I know I can upgrade glibc alone, but os team of my company don't allow me to upgrade it alone in case of some "unknown compatibility issues"...

>_<

---

### Post by guiverc on 2021-05-21
Release schedules are public, and actually published up to six months before development starts (*bionic's* was created 2017-May-25 but of course changed during its life cycle) ...  and can be seen at 

[https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule)

and no, 18.04.5 is the last scheduled ISO  (18.04.5 was when it got it's final HWE 5.4 kernel, ie. the stack from the 20.04/*focal* release)

Yes 16.04.6 & 16.04.7 were created, [however weren't scheduled]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule").  They however were created because the release hadn't reached ESM & new installation media was needed because of SHIM & like updates (*security fixes to enable install*).  That is a very different issue to a system library that can be fixed via upgrade post-install though.

---

### Post by Impavidus on 2021-05-21
I don't get it. Do you mean the os team of your company forbids you to install any updates after initial installation of the os? That sounds like a really bad idea. Or just the security updates? If you install the regular updates (I don't even think about not doing that), you should already have 2.27-3ubuntu1.4. Indeed, that fixed version of glibc is not in any of the live disk images. New live disk images are released to fix critical bugs in the live disk or to make it work on more recent hardware, not to distribute bugfixes to installed systems, but by now nobody installs 18.04 on the latest hardware, as we have 20.04 for that. So no more live disk images are planned for 18.04.

---

### Post by rsteinmetz70112 on 2021-05-21
By far the best method of keeping Ubuntu current is to do regular updates. I generally do it about weekly. These are official patches and even if the package version number is not updated security and bug fixes are often back ported to the existing packages. You may find that the current repository version of glibc has that particular bug fixed. There is a place where this information is available, I don't remember where. If you have the bug description you can find if a simple update and upgrade will fix your problem.

---

### Post by guiverc on 2021-05-21
You didn't provide the CVE or bug that concerns you, so I answered on the ISO spin detail.

Security fixes are back-ported to supported releases, if you know the bug CVE you can see what package for any release that contains a fix, eg.

[https://ubuntu.com/security/cve](https://ubuntu.com/security/cve)

(*other like sites exists; but you didn't provide any specifics of your concern*)

---

### Post by iamacmol on 2021-05-25
Thank you. 
[URL="https://launchpad.net/ubuntu/+source/glibc/2.27-3ubuntu1.3"]
https://launchpad.net/ubuntu/+source/glibc/2.27-3ubuntu1.3[/URL]

    - pthread_cond_broadcast: Fix waiters-after-spinning case
this bugfix is what I want.


I've tried harder to persuade the os team of my company to upgrade glibc,  they agree to do this after seeing this thread.

3Q~

---

