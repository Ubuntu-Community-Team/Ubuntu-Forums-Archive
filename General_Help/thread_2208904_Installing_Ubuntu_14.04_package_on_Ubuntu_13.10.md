---
title: "Installing Ubuntu 14.04 package on Ubuntu 13.10"
date: 2014-03-02
forum: General Help
---

### Post by BandC on 2014-03-02
Hi. Ubuntu 13.10 has tesseract package 3.02.02 but I need the newest version which is 3.03.02. This newer version is set to be included in Ubuntu 14.04 as seen the output below:

ubuntu:~$ rmadison -u ubuntu tesseract-ocr
 tesseract-ocr | 2.04-2    | lucid/universe   | amd64, armel, i386, ia64, powerpc, sparc
 tesseract-ocr | 3.02.01-2 | precise/universe | amd64, armel, armhf, i386, powerpc
 tesseract-ocr | 3.02.01-6 | quantal/universe | amd64, armel, armhf, i386, powerpc
 tesseract-ocr | 3.02.02-1 | saucy/universe   | amd64, armhf, i386, powerpc
 tesseract-ocr | 3.03.02-3 | trusty/universe  | amd64, arm64, armhf, i386, powerpc, ppc64el

My question is: how can I install this new version on my 13.10 without breaking anything (now or when it's time to upgrade to 14.04)? I don't want to wait until April if I can help it. Is it possible?

Thanks.

---

### Post by Tristan_Williams on 2014-03-02
It is really dangerous to mix releases like that. This is because 13.10 packages rely on 13.10 toolchains, certain packages etc...
14.04 packages do the same thing. So if you mix the releases, half of the packages would think that the other half is missing. 
It would be a constant battle of installing, removing, upgrading, and reinstalling packages.

You can find the PPA, Dependency PPA, and installation instructions in the following links:
[https://launchpad.net/~gezakovacs/+archive/tesseract](https://launchpad.net/~gezakovacs/+archive/tesseract)
[https://launchpad.net/~gezakovacs/+archive/builddeps](https://launchpad.net/~gezakovacs/+archive/builddeps)
[http://ubuntuforums.org/showthread.php?t=1647350](http://ubuntuforums.org/showthread.php?t=1647350)

Also, once you upgrade to 14.04 after its realease, you can remove the PPA, and reinstall it via the Trusty repos

---

### Post by monkeybrain20122 on 2014-03-03
> **Tristan_Williams said:**
> 

Also, once you upgrade to 14.04 after its realease, you can remove the PPA, and reinstall it via the Trusty repos

You get the order wrong. You have to remove all ppas (and probably downgrade the packages) **before** "upgrade" or you run a high risk of blotching the upgrade.  "Upgarde" assumes you have a fairly pristine system (no ppa, no proprietray driver, no third party software). Thus IMO it is always easier, safer and A LOT faster to simply backup your data and do a clean install. "upgrade" is very problematic.

---

### Post by frank18 on 2014-03-03
I also Upgraded from Ubuntu 13.10 to 14.04 and so far have no issues,a matter fact the mouse in  xbmc in 13.10 did not work right and now in 14.04lts it's ok.

---

### Post by frank18 on 2014-03-03
> **frank18 said:**
> I also Upgraded from Ubuntu 13.10 to 14.04 and so far have no issues,a matter fact the mouse in  xbmc in 13.10 did not work right and now in 14.04lts it's ok.
  

I followed these instructions.



[http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/](http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/)

---

### Post by monkeybrain20122 on 2014-03-03
> **frank18 said:**
> I fallowed these instructions.



[http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/](http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/)

Yeah and that takes hours and chances are it will screw up your system (just check how many bad upgrade related threads here)

 *if you have to do that because you are too lazy to back up your data and spend 20 minutes on a clean install make sure you revert your system to a 'clean state' (disable/purge all ppas, remove  proprietary graphic driver) before you proceed. Can't believe these people writing tutorials on upgrading Ubuntu without even at least a warning on this point (and the long time it takes). I wonder if they actually have done it themselves or just cut and paste from official documentations.

---

