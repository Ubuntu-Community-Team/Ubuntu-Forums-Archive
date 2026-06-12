---
title: "Firefox and flash issues"
date: 2008-01-14
forum: General Help
---

### Post by pdusen on 2008-01-14
Ok, I went to a website that used flash and was prompted to install either the Flash of Gnash plugin, as expected. In my previous install I used the Flash plugin, and decided to go with that again in this one. 

However, upon install, Firefox still wouldn't recognize flash videos. I double-checked in Synaptic to make sure the package was installed. So at this point I decided to try out Gnash, and it also installed. However, I am having the exact same problem still; Firefox keeps prompting me to install one or the other, and I've already installed both.

Is there something I'm missing here?

---

### Post by tgalati4 on 2008-01-15
View-->Page Source  and take a look at the code.  Perhaps you can determine what format the videos are really being streamed in.

If you provide us a link to the site that you are having trouble with perhaps we can test it ourselves.  I'm using Linux Mint 4 XFCE and I have yet to encounter a flash site that doesn't work.

---

### Post by pdusen on 2008-01-15
It's no one page, it's any page with a flash part of it; for example, youtube videos.

I didn't have this problem before either, but I reformatted recently and for inexplicable reasons it isn't working now.

---

### Post by zipperback on 2008-01-15
> **pdusen said:**
> It's no one page, it's any page with a flash part of it; for example, youtube videos.

I didn't have this problem before either, but I reformatted recently and for inexplicable reasons it isn't working now.

don't install both gnash and flash. You should not have both plugins loaded.

Are you running 32bit or 64bit? If it's 64bit then there is some extra work involved.

See this page for 64bit users.
[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+plugin](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+plugin)

If it's 32bit...

Install the flash plugin using synaptic.

If it won't install, then read the information on the following page.

[http://ubuntuforums.org/showthread.php?t=636397&highlight=flash+plugin](http://ubuntuforums.org/showthread.php?t=636397&highlight=flash+plugin)

- zipperback
:popcorn:

---

### Post by Max_rulez on 2008-01-15
thanks for asking i was just about to do the same

---

### Post by eggdeng on 2008-01-15
Type ```
about:plugins
``` in Firefox's address bar to see a list of installed plugins. If you don't see ```
libflashplayer.so
``` then it has probably installed to the wrong place. If it is present, under Edit->Preferences->Content->Manage, check that it is set to open .swf and .spl files.

---

### Post by Max_rulez on 2008-01-15
and it worked 2 thx guys

---

