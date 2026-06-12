---
title: "'xgamma' help, please!"
date: 2007-06-29
forum: General Help
---

### Post by AlexMacInnis on 2007-06-29
Sorry, first time Ubuntu user here!

I'm trying to run 'xgamma' in the terminal to increase the gamma (my monitor stinks), and I get this message:

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Unable to query video extension version

What does it mean and how do I go about fixing it?

Warning in advance: jargon won't mean much to me, so layman's terms please! ;)

---

### Post by AlexMacInnis on 2007-06-30
Bump.

I just installed KDE and the "xgamma" command works fine for it, but whenever I want to use Ubuntu, it doesn't let me.

Any ideas or workarounds?

I added "Gamma 2.2" to the "Monitor" section of xorg.conf, but I don't think that's done anything.

Help would be greatly appreciated!

---

### Post by Theosa on 2008-05-06
The section is corret, but no quotation marks. =)
Gamma 0.80

After you restart xorg, fire up a terminal and write xgamma. Check the results.

Cheers!

---

