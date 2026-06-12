---
title: "Window Title Missing xorg.conf problems"
date: 2007-10-20
forum: General Help
---

### Post by YetAnotherNoob on 2007-10-20
I am a noob and this is a whine.  I have just spent 2 hours attempting to fix a problem with the window manager not working properly.

It occurred after I had restarted the session CTRL+ALT+BACKSPACE.
A later reboot then started showing an nVidia splash screen (never seen before) and a login screen with a lower screen resolution than normal.
Once logged in the problem was window title bars, and various other controls were missing (terminal windows blank etc).

I am running Gusty Gibbon.  I went to System>Preferences>Appearance>Visual Effects and turned it down to None.  The window title bars returned but I had no sexy effects!

I immediately loaded Firefox and searched for a resolution.  Other people had what sounded like similar problems and recommended various things:
deleting gnome session files
reinstalling beryl
reinstalling emerald
playing with nvidia-settings
changing color depth
fiddling with synaptic
reinstalling compiz
blah
blah

As I have already said I am new, none of these things meant anything to me whatsoever.  I tried some of them...and made things worse.

Eventually I overwrote my xorg.conf file with a backup copy xorg.conf1 and everything was magically back to the original.
Gaaaa!  :confused:
Honestly what kind of window manager is so easily corrupted? :(
Anyway, I hope this helps someone.

---

