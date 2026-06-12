---
title: "NVidia Security bug"
date: 2006-10-23
forum: General Help
---

### Post by hinne on 2006-10-23
Just wondering what people think of this (I have my own thoughts, though no simple answer).

There is a known bug in the nVidia binary video driver according to security firm [rapid7]("http://download2.rapid7.com/r7-0025/"). Apparently this issue has been known since late 2004 and requires a user to visit a malicious website to be exploited. Rapid7 recommends users switch to the 'nv' driver since that is not vulnerable.

Many of us now run Beryl or XGL which relies on nVidias binary driver to enable the required 3d effects--to my knowledge beryl won't work with the 'nv' open source driver.

So the problem is that we can (i) shut off beryl and use the 'nv' driver till nVidia fixes this problem,  (ii) take the risk and only visit trusted websites (even though these could be hacked and be hosting malicious exploits) (iii) use something other than nvidia.

I think this case illustrates perfectly the weaknesses of the closed source model (i.e. one vendor taking very long to fix a known problem) and the risks of closed source drivers in an open source platform.

But I also think it needs a pragmatic solution. Any thoughts? Do we / can we put the blowtorch on nvidia to get this fixed?

---

### Post by ~LoKe on 2006-10-23
I haven't been following the situation, but I would assume that if it has been known since 2004, if it were possible, someone would have exploited it publicly by now, which, IIRC, hasn't happened.

There are often reports of "possible malicious exploits" that require certain impossible or unlikely conditions to be met.

I wouldn't worry about it, honestly.

---

### Post by hinne on 2006-10-23
I tend to disagree...an exploit would more likely than not install a rootkit first and other malware later. Most Linux users do not use AV and an issue like this can stay under the radar for quite a while.

Another point is that the recent advisory (17 October) comes with full exploit source code which I think raises the urgency of the issue somewhat.

CHANGED: I wrote I agree with the previous poster, but didn't actually. Should have read his entire post before posting back... I think this is an issue to worry about. Until the release of XGL I never bothered with nVidia's driver, but now use it because I like beryl.

---

### Post by drumour on 2006-11-05
Linux Security has more info on this with a link to Security Focus. There is also a link to a petition to get Nvidia to get their act together (2000 odd signatures so far)  see:

 [http://www.linuxsecurity.com/content/view/125305/91/](http://www.linuxsecurity.com/content/view/125305/91/)

---

