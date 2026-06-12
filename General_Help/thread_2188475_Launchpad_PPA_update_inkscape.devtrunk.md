---
title: "Launchpad PPA update: inkscape.dev/trunk"
date: 2013-11-17
forum: General Help
---

### Post by zaleksf on 2013-11-17
I'm running Xubuntu-13.10_x64 with a few PPAs along with the regular software repositories.

I seem to be getting regular updates from a few of my PPAs, but possibly not from all. For instance, I am definitely getting updates from ppa:sebikul/gambas-daily and ppa:jtaylor/ipython-dev. 

However, it seems that I am not getting updates from ppa:inkscape.dev/trunk. My inkscape package is 'stuck' at 1:0.48+devel+**12700**+44~ubuntu13.10.1 , wheareas the PPA site indicates that it should be 1:0.48+devel+**12816**+44~ubuntu13.10.1.

I have tried changing repository mirrors, uninstalling and reinstalling the packages, reinstalling the PPA, etc. Is there a way to determine if the problem is on my end, or with the PPA site? Would it have to do with the fact that ppa:inkscape.dev/trunk packages rely on libcairo2 version 1.12.16-**0ubuntu1~ubuntu13.10.1**, whereas the the current 13.10 libcairo2 version is  1.12.16-**0ubuntu2**?

Thanks in advance.

Never mind - digging a little deeper into the PPA showed that the latest version of inscape (12816) failed to build; this was not obvious from the main site page.

---

