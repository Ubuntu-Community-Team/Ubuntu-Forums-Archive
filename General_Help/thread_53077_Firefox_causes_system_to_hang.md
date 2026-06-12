---
title: "Firefox causes system to hang"
date: 2005-07-30
forum: General Help
---

### Post by JmSchanck on 2005-07-30
On several occassions now my computer has become almost completely unresponsive after visiting a webpage in firefox. It feels like its stuck in a loop, i can move the mouse but clicking has no effect, It wont switch to a vt when i press ctrl-alt-f1 and ctrl-alt-backspace has no effect either, so the only option is to hard reboot the computer. Its been very difficult to replicate until just now, its done it twice on a download page at sourceforge when I use the easynews mirror. [here [SourceForge.net]](http://prdownloads.sourceforge.net/jirr/jirr_0_4_src.zip?download). Can anyone see a reason this might be happening, it becomes unresponsive too quickly for me to check the page for what might be causing it, possibly a faulty plugin or something? Any help is greatly appreciated, thanks.

---

### Post by bunced on 2005-08-01
OK. A couple of questions:

1) Does it happen always on the same page?

2) Does it follow a regular pattern

3) Have you updated Xorg or manually edited xorg.conf. Very often, it could be Xorg that is doing it.

4) Have you updated Firefox.

You should also disable all extensions and then browse for a couple of days. Then enable them one by one, doing lots of browsing in between. That should find your problem

Regards,
David

---

