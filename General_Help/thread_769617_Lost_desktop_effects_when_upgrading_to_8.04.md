---
title: "Lost desktop effects when upgrading to 8.04"
date: 2008-04-26
forum: General Help
---

### Post by jkratze1 on 2008-04-26
Anyone else lose desktop effects?  How do I get them back. All was well with Ubuntu 7.10 while using the ATI open source drivers.  I upgraded and now desktop effects cannot be enabled. I have an ATI Mobility 9600.  Please help me get my desktop effects back.

---

### Post by LaRoza on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Maybe that will help.

---

### Post by Toxicity999 on 2008-04-26
The previous poster is most likely correct. Though compiz can be run on pretty much any remotely modern 3D accelerator, to maintain visual quality, and framerate, it's not always the compiz we all know and love, having to disable things.

The graphics card check is there to assume maximum stability and quality. Just keep that in mind.

That said, if it works, it works =]

---

### Post by jkratze1 on 2008-04-26
> **LaRoza said:**
> [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Maybe that will help.

Thanks LaRoza bigtime.  I added the SKIP_CHECKS="yes" to the top of /usr/bin/compiz as suggested in the link and now I can enable compiz in 8.04. \\:D/

Such a simple fix to get desktop effects working again.  This forum is such a great resource.

---

