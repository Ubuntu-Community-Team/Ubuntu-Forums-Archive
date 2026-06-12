---
title: "RealPlayer plugins"
date: 2005-09-20
forum: General Help
---

### Post by baldwin8 on 2005-09-20
I downloaded and installed RealPlayer 10 and and trying to figure out one problem. I use it with Firefox to listen to the BBC and can listen live using RealPlayer as a standalone player. But when I try to listen to the "listen again" programs, nothing reacts. What should I be seeing for plugin permissions in the files that are in the Firefox plugins folder? I have the two plugins in the Mozilla folder.

Thank you

---

### Post by Holdem on 2005-09-20
I had the same problem but I followed this and all was well.
[http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml)

---

### Post by skoal on 2005-09-20
I installed the Realplayer binary as well.  Here's what you need (for plugins to work):
```
skoal@morpheus:///usr/lib/mozilla-firefox/plugins $ ls -l
total 0
lrwxrwxrwx  1 root root 40 2005-09-20 11:32 flashplayer.xpt -> /usr/lib/mozilla/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root 42 2005-09-20 11:32 libflashplayer.so -> /usr/lib/mozilla/plugins/libflashplayer.so
lrwxrwxrwx  1 root root 42 2005-09-20 11:32 mplayerplug-in.so -> /usr/lib/mozilla/plugins/mplayerplug-in.so
[COLOR=DarkRed]lrwxrwxrwx  1 root root 35 2005-09-20 11:32 nphelix.so -> /usr/lib/mozilla/plugins/nphelix.so
lrwxrwxrwx  1 root root 36 2005-09-20 11:32 nphelix.xpt -> /usr/lib/mozilla/plugins/nphelix.xpt[/COLOR]
lrwxrwxrwx  1 root root 33 2005-09-20 11:32 nppdf.so -> /usr/lib/mozilla/plugins/nppdf.so
```
* You'll notice that these .so files (in the mozilla-firefox folder) are just symlinks to the actual plugin .so files (in the mozilla folder).  I leave the actual plugins in the mozilla folder and just symlink them again in the firefox folder.

\\//_

---

