---
title: "Xfce and a White Screen of Death."
date: 2008-06-23
forum: General Help
---

### Post by lelizondob on 2008-06-23
I installed Xfce (xubuntu-desktop) and I liked it. Everything was working fine, even compiz was enabled and working. Suddenly and after a reboot when I logged in to xfce all I've got was a white screen, and all it worked was the 3d cube, I could see when xfce starts, everything seems fine for about 5-10 seconds and then, the white screen (for sure of Death).

I followed a couple of post in the forum that seems to fix my problem but no luck.

So I removed xubuntu-desktop and all xfce related stuff. Even erased the xfce config files in my home directory. Installed again but nothing, this time compiz hasn't been enabled (because I can't) and all I get is the white screen. Somebody said in a forum post that after 3 times he/she logged in and kill X, He/She was able to get xfce working. that didn't work for me.

So what can I do after I even removed, erased the config files and installed again? I love Gnome but Xfce it's so much faster. I'm using Hardy (upgrade from Gutsy) and my Video Card is working with Gnome.

thanks in advance

Luis

---

### Post by mali2297 on 2008-06-23
I assume Gnome works, right?

Perhaps you have missed some configuration files. Besides those in ~/.config, you should also erase the directory ~/.cache.

---

### Post by lelizondob on 2008-06-23
Yes, Gnome works with compiz enabled. I didn't erased the .cache directory, I'll try and let you know... Thanks.

Luis

---

### Post by lelizondob on 2008-06-23
No. It didn't work. When I log in I see the desktop wallpapper, the panel and the icons for about 5-10 seconds and then the white screen. This time, for some reason compiz got enabled (don't know how). Shouldn't be disabled because there's no config files for the xfce?

Any other directories I should get rid off?

Luis

---

### Post by mali2297 on 2008-06-23
From a terminal, type
```

sudo /etc/init.d/gdm stop

```
That should get you to a command line prompt on the console (otherwise press Ctrl+Alt+Backspace). From there, run
```

startxfce4

```
Any luck?

If it doesn't work, you can get back to the graphical login screen with
```

sudo /etc/init.d/gdm start

```

---

### Post by lelizondob on 2008-06-23
It does work when I run startxfce4. I also erased the following directories:

.cache/xfce4
.cache/sessions/xfce*
.config/xfce4
.config/xfce4-session

After I rebooted I could use the graphical login to get into xfce. Even compiz is enabled and working.

Thanks a lot.

Luis

---

