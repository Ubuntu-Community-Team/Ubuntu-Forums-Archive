---
title: "Need instructions to make sane-backends cvs snapshot"
date: 2008-06-12
forum: General Help
---

### Post by jeffk on 2008-06-12
Per upstream maintainer calls for testing, I'd like to test current cvs snapshots of sane-backends with my Fujitsu scanners.

Is there a detailed procedure to follow to make a compliant sane-backends package directly from a CVS snapshot tarball?

I want it to be as close to the eventual .deb ubuntu package as possible, including any ubuntu-specific patching.

Thanks.

---

### Post by jeffk on 2008-09-08
Replying to an old post, revised subject.

My bug report remains untriaged:
[URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/233976"]
Double-free following scan on ubuntu hardy 8.04 with epjitsu fi-60f[/URL]

And I'll be onsite with the fi-60f in question tomorrow on an unrelated support call.

> The backend author quickly made the following commits to CVS in response to the report:

[epjitsu.c.diff]("http://alioth.debian.org/plugins/scmcvs/cvsweb.php/sane-backends/backend/epjitsu.c.diff?cvsroot=sane&r2=1.6&r1=1.5&f=u")

[epjitsu.h.diff]("http://alioth.debian.org/plugins/scmcvs/cvsweb.php/sane-backends/backend/epjitsu.h.diff?cvsroot=sane&r2=1.3&r1=1.2&f=u")


I'd very much like to test a patched sane-backends-1.0.19-1ubuntu3.deb, but haven't had time and avaialble systems to learn how to make simple patched .debs. My packaging experience has been with Gentoo ebuilds.

Can anyone list a step-by-step for this case, so I can take advantage of the onsite time to test, and update that bug report?

Thanks.

---

