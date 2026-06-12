---
title: "tdfx not able to use higher resolution than 800x600"
date: 2007-03-22
forum: General Help
---

### Post by MrNatewood on 2007-03-22
Hello,
I have encountered the known bug of tdfx crashing X in Edgy. So I temporarily changed the driver in xorg.conf to "vesa" and it worked in all resolutions. But with vesa the scrolling is very choppy so I searched a solution for tdfx to work. I have found on launchpad someone(audiophyl) that wrote a step-by-step to update the driver to a newer version([https://launchpad.net/ubuntu/+source/xorg/+bug/68291/comments/20](https://launchpad.net/ubuntu/+source/xorg/+bug/68291/comments/20))

I have followed what he wrote and tdfx now is loading but cannot work at a higher resolution than 800x600(the higher resolutions simply do not appear in System->Preferences->Screen Resolution). 1024x768 and 1280x1024 are specified in xorg.conf. I should note again that with "vesa" these resolutions work.

Does anyone have a solution to this problem?

---

### Post by MrNatewood on 2007-03-22
*bump*

---

