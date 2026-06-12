---
title: "prefetch package, unable to locate"
date: 2007-06-16
forum: General Help
---

### Post by GXP on 2007-06-16
The other day I was reading 'The sysadmin's toolkit' in LXF93 (LinuxFormat Issue 93, June 2007) and one of the articles mentioned the package prefetch. What made me want to install it was the magazine staff was able to load OO Writer in 8.9 seconds versus 25+ seconds.

Since I have a Celeron processor (500Mhz) I thought I would give it a try to see if I could get a similar reduction. (Sidebar - 7.04 is extremely efficient on this hardware and runs faster than 5.10 or 6.06, at least in my experience  - but YMMV.)

First I do an apt-cache search to see if it's in the respo's, not there. Then I head on over to sourceforge.net, again not there. Google searching only brings me squid-prefetch, which is a different package. Google again -squid but no relevant results. Did a search in the forums before posting and even looked at the Debian & Fedora repositories. This package doesn't seem to exist. What am I missing?

Does anybody use the package 'prefetch' and were do I find it? Is it part of some other package?

Thanks in advance.

---

### Post by GXP on 2007-06-16
Giving a gentle bump.

What other locations might I try to find packages? I am not adverse to hunting for this if somebody could point me in a direction...

---

### Post by david_2001 on 2007-06-16
> **GXP said:**
> Giving a gentle bump.

What other locations might I try to find packages? I am not adverse to hunting for this if somebody could point me in a direction...
Did you not mean *prelink*, as described on page 42 of LXF93?  It's in the Ubuntu universe repository.

---

### Post by GXP on 2007-06-16
> **david_2001 said:**
> Did you not mean *prelink*, as described on page 42 of LXF93?  It's in the Ubuntu universe repository.

Yes! *prelink*, makes sense now why I could not find it. Tried to remember to many things from that issue while on lunch. Guess I messed that one up :p .

Thank you for the assistance.

---

