---
title: "Reverting to kwin from compiz-fusion, default window manager?"
date: 2008-06-01
forum: General Help
---

### Post by mainstreetexile on 2008-06-01
Can anyone tell me where to specify the default window manager for kubuntu?

I was having problems with compiz-fusion crashing on an i810 (lose all window decorations maximize, minimize, couldnt alt-tab between windows or get a run box to fix it).

The only information I found was using kwin --replace and then killing compiz once it's started but I can't seem to find any information on where to specify the default windows manager to kwin at startup.

I'd like to keep compiz on here so i can 'compiz --replace' to play around when i want but i need the stability of kwin since compiz is still too buggy for my purposes.

Any help would be greatly appreciated?

---

### Post by Cresho on 2008-06-01
why dont you try building scripts and auto start them up?  It is very simple.

---

### Post by mainstreetexile on 2008-06-01
hi, thanks for the reply. i made a "kwinswitch.sh" bash script to do the kwin --replace and killall compiz but it seems like a bit of a hack to have compiz start up as the default just to then kill it and switch with my bashrc.

I couldnt figure out where the KDEWM variable was getting set but I found my answer <a href="https://bugs.launchpad.net/ubuntu/+source/desktop-effects-kde/+bug/218180">here.</a>

pretty much boils down to:

<pre>
/etc/X11/Xsession.d/25enable-compiz

The contents of this file test for a hidden configuration file in the users home directory:

$HOME/.kde/share/config/compizasWM

And if it exists, it exports the KDEWM variable to be /usr/bin/compiz.
</pre>

I just moved the compizasWM file out of that directory and now kwin starts as default but i can still do compiz --replace if i want to.

---

### Post by ajgreeny on 2008-06-01
If you really can't use compiz on your machine have you considered uninstalling all compiz apps on the computer?  I'm sure that would do it.

---

### Post by Cresho on 2008-06-01
> **mainstreetexile said:**
> hi, thanks for the reply. i made a "kwinswitch.sh" bash script to do the kwin --replace and killall compiz but it seems like a bit of a hack to have compiz start up as the default just to then kill it and switch with my bashrc.

I couldnt figure out where the KDEWM variable was getting set but I found my answer <a href="https://bugs.launchpad.net/ubuntu/+source/desktop-effects-kde/+bug/218180">here.</a>

pretty much boils down to:

<pre>
/etc/X11/Xsession.d/25enable-compiz

The contents of this file test for a hidden configuration file in the users home directory:

$HOME/.kde/share/config/compizasWM

And if it exists, it exports the KDEWM variable to be /usr/bin/compiz.
</pre>

I just moved the compizasWM file out of that directory and now kwin starts as default but i can still do compiz --replace if i want to.

that is sweet!  I tried kde4 a while back and just figured I'll wait until they update it.  It looks promising. From experience, compiz stands light years ahead of it.  Using KDE4 was like trying to force a mule to move.  It has many features yet to be revealed.  I like the default icons and interface though.  I know it will graduate from a mule to a horse.

---

