---
title: "Installing Catalyst 15.9 drivers"
date: 2015-09-18
forum: General Help
---

### Post by XBMC old School on 2015-09-18
I don't have any issues  yet because I haven't installed the drivers. Is there a good tutorial on how to explicitly install these drivers. I have had issues with it before, and have elected to not install them. Do I just install all of the .debs from the AMD page [here]("http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64")?

Instead of waiting until after my problems arise, I was hoping to get ahead of it. Is there a guru around for this? My setup is in my signature.

Thanx.

---

### Post by QIII on 2015-09-18
Were I you, I would use the fglrx driver available in the repo for your release.

It is exactly the same driver as was available from AMD at the time of the Ubuntu release, but has been tested and packaged for Ubuntu.

Unless there is a compelling reason to have the absolute latest driver, it is not worth the possible frustration.

I hope that you are not actually using 13.10 as you have indicated at the right of your header.  That release is well beyond End of Life.

---

### Post by XBMC old School on 2015-09-20
Thanks Qiii,

I have seen a few posts were people had issues with the package not installing properly from the repos and I wanted to avoid it. But I found [this tutorial]("http://linustechtips.com/main/topic/246639-installing-catalyst-on-ubuntu/?p=3385296") but it is out of date, I was unsure that the WGETs would be the latest and appropriate to my OS install.

---

