---
title: "How to Get Keyboard Shortcut to Open Right Music Player?"
date: 2006-10-19
forum: General Help
---

### Post by Ubuntist on 2006-10-19
Having buttons on my keyboard for controlling a music player, I've used System|Preferences|Keyboard Shortcuts to configure them.  They work, except that the button for opening a music player opens the RhythmBox player, when, most of the time, I'd rather use Quod Libet or Amarok.

Would anybody know how I could change the player opened by the button?

---

### Post by Ubuntist on 2006-10-23
OK, my quick and dirty fix is to remove RhythmBox and install in /usr/bin/local a file called "rhythmbox" which simply executes the command "quodlibet", my preferred music player.

This is obviously a bit inelegant; anybody have a better idea?

*Somebody *must know how to change the command executed by the "music" button on the multimedia keyboard.

---

### Post by smithveg on 2006-10-24
yeah, i'm looking for this solutions.

I had uninstall Rhythmbox from my systems, and installed xmms.
But when i press a music button, it always prompt me 'Rhythmbox not found'. Anyone know how to make the button point to 'xmms player'.

Thanks.

---

