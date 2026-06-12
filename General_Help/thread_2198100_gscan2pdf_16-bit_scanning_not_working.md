---
title: "gscan2pdf 16-bit scanning not working"
date: 2014-01-07
forum: General Help
---

### Post by kayvee on 2014-01-07
I have a Canon LiDE 100 flatbed scanner that is capable of 16 bit scanning. And I am able to scan images using either Skanlite or scanimage at the 16 bit depth. However, when I use gscan2pdf, the scanned output is just gray dots with nothing else visible as shown below:
[ATTACH=CONFIG]249286[/ATTACH]
Gscan2pdf outputs correct images when used at 8 bit depth as shown below:
[ATTACH=CONFIG]249285[/ATTACH]
I see this behavior with both libsane-perl and scanadf backends. scanadf-perl does not appear to be working on my computer (it falls back to libsane-perl every time I try to use it) and scanimage does not even give me the option of bit depth. Is this a bug? Or do I need to install anything else for it to work? Sample images are attached.

---

