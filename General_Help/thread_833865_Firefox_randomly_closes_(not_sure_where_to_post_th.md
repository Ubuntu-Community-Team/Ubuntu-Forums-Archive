---
title: "Firefox randomly closes (not sure where to post this)"
date: 2008-06-19
forum: General Help
---

### Post by Deutscher Alex on 2008-06-19
When I move between my workspaces, my Firefox windows in the workspace I am switching from sometimes close. This almost always happens when the Firefox window is loading a page, or for that matter an ad is refreshing itself.
Also, when restoring Firefox's session after a shutdown, all these windows open for a few seconds and then disappear, only to reappear the next time I do 'restore session'. It seems that these windows don't actually CLOSE, only disappear, because when I close all remaining Firefox windows, the Firefox.exe (I'm running Firefox 2.0.0.14 through wine >.>) process stays active in my System Monitor. This problem started off only happening in my Windows version of Firefox, but now it also happens with Ubuntu's preinstalled Firefox 3.0, so it shouldn't be an issue with wine....

---

### Post by Deutscher Alex on 2008-06-19
...bump

---

### Post by Deutscher Alex on 2008-06-19
It also seems that when firefox 2.0.0.14 is open (with about 20 disappearing windows) that my 4 cpu's go to about 60% usage each. That's quite a lot considering firefox 3.0 by itself only makes 2 cpu's go to about 20% each, and the other 2 stay at 0%

---

### Post by Jaxilian on 2008-06-20
I got same problem.....but I have had this problem on all Firefox versions.

---

### Post by Deutscher Alex on 2008-06-20
> **flodis said:**
> I got same problem.....but I have had this problem on all Firefox versions.

so then we know it's certainly not a wine issue...


Heh it was starting to make my computer lag, what with 20 windows, half of which had java applets with sound which I couldn't mute without the master mute button....

---

### Post by Deutscher Alex on 2008-06-21
bump.... need a solution

---

### Post by Deutscher Alex on 2008-06-21
bump #4.

---

### Post by Deutscher Alex on 2008-06-23
bummpppp
nobody has a solution??

---

### Post by Deutscher Alex on 2008-09-21
...bump

---

### Post by MetalFanLiam on 2008-09-21
Have you installed the flash plugin? When i installed that, it seemed to close my firefox whenever there was any flash content on the page i was searching. If you have installed it, i suggest reinstalling it. This also applies to any other extentions or plugins you have installed.

You could use a different web browser, like opera or konquerer, but if thats not an option for you, run firefox in terminal using the 'firefox' command, then make it close (by doing the usual things that make it close) and see if the terminal has any output, and if so, post it back here.

Liam

EDIT, noticed you are using WINE, since it happens to your Ubuntu Firefox too, use your Ubuntu version and then do what i suggested, and we could maybe see whats causing your problems and try solving them on both WINE and Ubuntu versions

---

### Post by Deutscher Alex on 2008-09-22
running firefox through the terminal gave me this when it crashed:
```
java_vm: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Resource temporarily unavailable

```

---

### Post by mb_webguy on 2008-09-22
I can't answer why this is happening with the Windows version of Firefox under Wine, but with the Linux version of Firefox this issue is almost always due to problems with the Flash plugin.  Installing the Flash 10 plugin (either from the backports repository or by following the PulseAudio fixes link in my signature) usually fixes the problem.

---

