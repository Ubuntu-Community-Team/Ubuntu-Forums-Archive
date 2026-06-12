---
title: "Movies use 100% CPU"
date: 2004-11-16
forum: General Help
---

### Post by HungSquirrel on 2004-11-16
When I first installed xine-ui, totem-xine, the w32codecs, libdvdcss2, etc., my movies played fine. Now, just recently, movies have started to use more CPU time than they should. The larger I make the window, the more CPU time they use, getting up to 100% CPU usage when I make the window fullscreen. Once my CPU reaches 100%, I of course start seeing the framerate dropping (in fact, xine-ui will close because of it).  This happens when playing movies of any type. This continues to happen after I removed the packages and re-installed them.

Anybody have any ideas what may be causing the problem? Could it be prelink? I started prelinking about a week ago following the HOWTO. That's the only thing I can think of that may be causing it, but I also followed the instructions for disabling prelink and that didn't help either.

---

### Post by Nikola on 2004-11-16
Start System Monitor and look what process is sucking CPU.

---

### Post by p!=f on 2004-11-16
Did you try to play movies in MPlayer or pure Xine? Just to see any difference.
 It happened here too (under MPlayer). Changing video output to x11 and sound output to oss got rid of it. Especially sound daemons may make slowdowns.

---

### Post by HungSquirrel on 2004-11-16
[QUOTE=Nikola]Start System Monitor and look what process is sucking CPU.[/QUOTE]
 Interestingly, XFree86.

I don't use MPlayer, but I have no sound daemons running.  Oddly, when I try to start esd I get this error (which I've never encountered before):

```
/dev/dsp: Device or resource busy
```

---

### Post by Nikola on 2004-11-16
/rant mode on/
I'm still waiting to see on Linux what I had on BeOS since r4 (Gee, how meny years ago)... On same PC (dual celeron 2x450Mhz) with 128MB (I have 256 now), double click on a movie, it would load instantly, I could play a dozen of clips simultaneosly with audio mixing, without freezing GUI.
On Linux, it's still far from perfect. Gstreamer, xine-lib, then ALSA, OSS, esd,.... I'm (almost) totaly lost. I've managed to make it work, but it's not even close to what BeOS could do 5 years ago.
/rant mode off/

---

### Post by HungSquirrel on 2004-11-17
Resolved.  Turns out I didn't have all the latest security updates, including some for X, because I had my ubuntu-security lines commented out in sources.list.  Now the movies are running as they should.

---

