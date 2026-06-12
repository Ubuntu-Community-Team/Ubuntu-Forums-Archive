---
title: "Problem with HTML rendering in Wine"
date: 2007-01-06
forum: General Help
---

### Post by Jammy_Stuff on 2007-01-06
I'm having a problem getting support for HTML rendering in Wine. I have tried both the build in the Ubuntu repository and the Wine official one. When I try to use something that would need to render, I get the box asking me to install Gecko (Mozilla) support. When I click install, all seems to go well but it doesn't work. When you look in the console, you see:

```
err:mshtml:InstallCallback_OnStopBinding Could not extract package: 80004005
Could not load Mozilla. HTML rendering will be disabled.
```

Anybody got any ideas?

---

### Post by shakin on 2007-01-09
The solution is on this forum, but it was hard to find so I'll post it here.

The file you need is wine_gecko.cab and you can get it from sourceforge here:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269)

or

[http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php)

Put that file into wine's Program Files directory and extract it (I used cabextract from the repositories). It will create a wine_gecko folder.

That's it!

I wonder why Wine doesn't come with it pre-installed or at least why the auto-install feature doesn't work.

Good luck!

---

### Post by cryolithic on 2007-06-21
I've tried this solution, as well as installing IEs4linux, as well as installing an older version of firefox for windows under wine, yet I still get the same message that HTML Rendering is disabled.

I'm not a linux newbie by any means, though this is the first time in years that I've attempted to install as my main desktop os.

FWIW I'm running Kubuntu, but I don't imagine that will make any difference for the rendering engine in wine ;)

---

### Post by ksudbury on 2007-11-18
Same problem after installing, this is a real pain tbh.

---

### Post by Elle Stone on 2008-01-22
Try going here:

[http://www.winehq.org/pipermail/wine-devel/2007-October/060193.html](http://www.winehq.org/pipermail/wine-devel/2007-October/060193.html)
for directions and here:

[http://www.winehq.org/pipermail/wine-devel/2007-October/060281.html](http://www.winehq.org/pipermail/wine-devel/2007-October/060281.html)
for a link to the gecko cabfile download.  

I created the folder /usr/share/wine/gecko.  Then I "wine_gecko-0.1.0.cab" and "wine_gecko.cab" in the gecko folder (there seem to be two different gecko cab files, three actually, all available at sourceforge - I don't know which of the two actually did the trick - the oldest is outdated and the other two are probably duplicates).

Then when I reran winecfg the complaint vanished.  Finally.

Elle

---

### Post by szandor on 2008-02-11
> **cryolithic said:**
> I've tried this solution, as well as installing IEs4linux, as well as installing an older version of firefox for windows under wine, yet I still get the same message that HTML Rendering is disabled.

I'm not a linux newbie by any means, though this is the first time in years that I've attempted to install as my main desktop os.

FWIW I'm running Kubuntu, but I don't imagine that will make any difference for the rendering engine in wine ;)

> **ksudbury said:**
> Same problem after installing, this is a real pain tbh.

i had to download the cab to /usr/local/share/wine/gecko/ not /usr/share/wine/gecko/

---

### Post by Doki on 2008-05-10
Well, thank you, it's worked well for me.
I had the problem while running Picasa 2 on my ubuntu hardy 64

---

### Post by DaVince21 on 2008-05-13
It didn't work at all for me, for either packages. I really don't have a clue why, and I'm also wondering why it's not just included with Wine...

---

### Post by DaVince21 on 2008-05-21
Well, nevermind. The Wine 1.0 Release Candidate automatically asks you to download the Gecko libraries as soon as you open an application that uses IE. Awesome.

---

