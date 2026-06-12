---
title: "Flash problems"
date: 2006-11-09
forum: General Help
---

### Post by Spug on 2006-11-09
I recently tried to upgrade my Mozilla-compatible Flash plugin to Flash 9 Beta, but that version didn't work right here. No Flash objects were displayed, the object areas were just gray in both Opera and Firefox. I've tried to install Flash 7 from Adobe's package, and that apparently makes Flash work slightly, as the Flash content is now completely black, but I can still click on and control the Flash in Opera if I know where buttons are and so on. Firefox just crashes now.

"flashplugin-nonfree" won't install - apt-get says "E: Package flashplugin-nonfree has no installation candidate".

"libflash-mozplugin" works badly on most sites (no anti-aliasing, black background instead of white), on some it's unsupported and on the ones where it actually works, it either crashes the browser (Firefox) or just halts (Opera) after a few seconds.                                                                                             
I tried uninstalling all plugins, going to a Flash site in Firefox and click "Download this plugin" on the broken
Flash movies, but after installing that, Firefox just crashes when trying to load a Flash file.

I don't know what other options I have left. I have no idea why Flash won't work whatsoever. The Adobe packages ar
e simple .so files that can be moved into plugin folders and deleted for uninstallation, so I don't see how they c
an have caused any problems.

Thanks for any and all help!

---

### Post by taurus on 2006-11-09
How did you install Flash 9 by hand?  All you have to do is to unpack it and move the libflashplayer.so to ~/.mozilla/plugins and you are all set!!!

---

### Post by Spug on 2006-11-09
Yeah, that was what I did :/ And that was how I tried to reinstall Flash 7 afterwards, too.

---

### Post by taurus on 2006-11-09
Start firefox and at the address bar/field, see which version of flash you are running/using.

```
about:plugins
```

---

### Post by Spug on 2006-11-09
Shockwave Flash 7.0 r68, which I just reinstalled because 9 was broken.

---

### Post by taurus on 2006-11-09
> **Spug said:**
> Shockwave Flash 7.0 r68, which I just reinstalled because 9 was broken.
What do you mean it's broken because I am using flash 9 right now with firefox?

---

### Post by Spug on 2006-11-09
I just mean that it didn't work. I know that it's supposed to work, just like 7 is supposed to work (I used it for months until I installed 9).

---

### Post by taurus on 2006-11-09
So you unpacked flash 9, removed the old version, moved the new libflashplayer.so to ~/.mozilla/plugins, opened up firefox and it crashed at some sites that require flash!!!

---

### Post by Spug on 2006-11-09
Yes. And after that, I also removed Flash 9, moved the Flash 7 libflashplayer.so to ~/.mozilla/plugins, opened up Firefox and it crashed. I've also tried out /usr/lib/mozilla/plugins, /usr/lib/opera/plugins and ~/.opera/plugins (the latter two for Opera, obviously), although Opera didn't crash, it just didn't work.

---

