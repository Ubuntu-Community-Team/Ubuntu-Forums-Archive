---
title: "Firefox Keeps Quitting!!"
date: 2005-10-31
forum: General Help
---

### Post by eyebrowman92 on 2005-10-31
After my firefox starts up and i click on a few links it quits. its done this about 10 times now. after i click on about 3 links itll quit when i click on the fourth one. whats going on?

---

### Post by jdong on 2005-10-31
Try starting Firefox by typing "firefox" in a terminal. Make it crash again. Does any new error messages get written to the terminal window?


Have you installed any new extensions recently?

---

### Post by majed on 2005-10-31
Did you install the flash plugin?

I noticed the same behaviour with the flash plugin from the repo.. 

i overcome my problem by installing firefox by downloading the tar file from mozilla.org and extracting it.. then installing the flash plugin using FF plugin tool.

---

### Post by ikd69 on 2005-10-31
I would bet on the flash plugin, too.  I have this problem as well on my amd64 box, not so on an older pentium 3 box.

I have tried several options:
(a) swfdec
(b) libpnflash
(c) chroot

In the end I opted to remove the flash plugin completely.

IKD

---

### Post by ofek on 2005-10-31
Had the same problem and switched to deer park beta and the problems are all gone. u should try to see if it does the trick for u 2.( u can download it from mozilla's site [www.mozilla.org](www.mozilla.org) )
p.s: in case u don't know deer park is firefox 1.5 that isn't out yet as a final version.

---

### Post by agds on 2005-11-09
It's reassuring to hear that 1.5 solves this problem.

---

### Post by eyebrowman92 on 2005-11-09
ive solved the problem by switching from the totem plug-in to the mplayer plug-in. who knows what totem was doing. also i cant figure out how to install 1.5. i only really know how to install stuff using a terminal or synaptic.

---

### Post by daigorobr on 2005-11-09
Unfortunately, 1.5 doesn't solve the totem plugin problem.
I can't even address a bug, since I don't have any clue of what's happening.

---

### Post by agds on 2005-11-10
Have you tried running it from a terminal window?  I was able to get some error info that way, but I never recorded it.  I solved the problem by removing the Totem plugin altogether.  It's just a matter of
```
cd /usr/lib/mozilla/plugins
sudo rm *totem*
```
which should delete all the files associated with Totem Mozilla Plugin.  Then I installed the mozilla-player package, which sets up Firefox to use MPlayer for embedded media.  With the exception of a couple of trailers at the Apple site, everything works perfectly now.

If, like me, you've been avoiding the MPlayer plugin because you didn't like the absence of controls and/or the inability to display video in full screen, those deficiencies have been addressed.

---

### Post by eyebrowman92 on 2005-11-10
ive removed totem and firefox doesnt quit but mplayer loads up extremely slow. is there any replacment for mplayer?

---

### Post by agds on 2005-11-11
There used to be a package called mozplugger that would let you use any player for embedded media.  I don't see it in the package lists anymore, so either it's no longer being developed or it hasn't made it to Breezy yet.

---

### Post by eyebrowman92 on 2005-11-11
alright ill just deal with mplayer. :(

---

