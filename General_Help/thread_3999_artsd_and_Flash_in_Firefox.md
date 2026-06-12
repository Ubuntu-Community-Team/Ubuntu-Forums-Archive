---
title: "artsd and Flash in Firefox"
date: 2004-11-11
forum: General Help
---

### Post by HungSquirrel on 2004-11-11
I installed artsd so I could hear multiple sounds at once (e.g. hear an IM while I am playing songs in xmms).  However, when I watch a Flash movie in Firefox, I have to kill artsd to watch the movie, then restart it so I can hear sound after I'm done.  Does anyone know of an easy way to get Flash and artsd to cooperate in Firefox?

---

### Post by mercurus on 2004-11-11
I haven't done any research into this particular issue, but I can guess the problem. If artsd has the sound device it won't let anything else access it, unless it is looped through artsd.

A couple of options:
1. See if the mozilla flash plugin or mozplugger can be configured to use artsd for audio output.
2. Check that OSS emulation is available and that artsd is listening for OSS and ALSA sounds. If flash is using OSS, then it should get looped through artsd.
3. Use esd rather than artsd. I imagine you're using KDE though, which makes artsd preferable.

Hope that helps
Cheers
mercurus

---

### Post by HungSquirrel on 2004-11-11
I am using artsd in Gnome.

I didn't know esd could play multiple sounds at once.  Thanks!

---

