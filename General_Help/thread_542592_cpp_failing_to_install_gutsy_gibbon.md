---
title: "cpp failing to install gutsy gibbon"
date: 2007-09-04
forum: General Help
---

### Post by zedstar on 2007-09-04
Hi.

I am having some problems installing a couple of packages on gutsy gibbon. Specifically cpp and gij:

dpkg: error processing /var/cache/apt/archives/cpp_4%3a4.1.2-9ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-alternatives: unknown argument `--quiet'

dpkg: error processing /var/cache/apt/archives/gij-4.2_4.2.1-5ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-alternatives: unknown argument `--quiet'

Could someone please advise me the best way to resolve this?

I have tried to manually edit out the offending --quiet and these packages installed but there seem to be more coming in using this. I guess I need to get hold of the update-alternatives binary which supports --quiet? What should I install/update? Any help much appreciated.

Thanks.

---

### Post by zedstar on 2007-09-04
Problem solved.

I had installed the Ipkg package management system and that had put its own update-alternatives into /usr/local/bin which was being picked up before the dpkg one.

---

