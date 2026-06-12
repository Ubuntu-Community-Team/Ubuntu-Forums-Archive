---
title: "Teamviewer and 16.10 don't get along"
date: 2016-10-20
forum: General Help
---

### Post by ken24 on 2016-10-20
I am having a difficult time getting Teamviewer to work on 16.10. I have downloaded the AMD64 and i386 architecture versions and both are giving dependency issues. Has anyone successfully gotten it going?

AMD64 fails due to a lib32asound2 dependency that I can't get to work and i386 fails due to a libpng12-0 which I am also having a hard to resolving.

Alternatively, are there any remote desktop applications that operate on Linux/Windows/Android and are portable on a USB for use on any computer? I haven't been able to find any other that crosses as many platforms.

(First post, so if anything is out of place, let me know. Thanks!)

---

### Post by Geoffrey_Arndt on 2016-10-21
If you're OK with using Chrome browser . . 

(is Cross Platform)   [https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp)

---

### Post by howefield on 2016-10-21
Seems that it can be made to work.

[https://ubuntuforums.org/showthread.php?t=2340067](https://ubuntuforums.org/showthread.php?t=2340067)

The real solution is for Teamviewer to release a build with libpng16.16 as a dependency instead of libpng12.0.

---

### Post by ken24 on 2016-10-21
I forced the dependencies when using dpkg and it runs mostly well. Visually, some icons aren't working, but no functionality is lost when remotely connected.

---

