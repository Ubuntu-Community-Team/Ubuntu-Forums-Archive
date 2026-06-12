---
title: "Sound Card Mysteriously Disappeared for No Reason"
date: 2007-08-30
forum: General Help
---

### Post by FreakyT on 2007-08-30
Hey all,

I have a Realtek AC'97 integrated sound card, which worked fine after I installed Ubuntu Feisty.  However, after rebooting the computer, I no longer get any sound from the card, and it doesn't even show up in the Gnome Mixer's list of sound cards anymore!

Any ideas?  Is there a way to force Ubuntu to re-run its sound card detection?

Or should I just switch back to XP? :(

EDIT:  Nevermind, I got it working.  The trick was to create a file called asound.conf in /etc with the text:
```

pcm.!default {
    type hw
    card ICH
}
ctl.!default {
    type hw
    card ICH
}

```

This apparently changed my soundcard back to the correct one.  Though I'm still confused as to why it would suddenly change in the first place...

---

### Post by ramjet_1953 on 2007-08-31
Navigate to [COLOR="Blue"]System>Preferences>Multimedia Systems Selecto[/COLOR]r and see if the card is listed in the dropdown menu.

If the [COLOR="Blue"]Multimedia Systems Selector [/COLOR]item is not in your menu, you may need to enable it by Navigating to [COLOR="Blue"]System>Preferences>Main Menu.
[/COLOR]
When the window opens, use the left panel to [COLOR="Blue"]navigate to System>Preferences[/COLOR]

Make sure that there is a [COLOR="Blue"]tick [/COLOR]next to Multimedia Systems Selector in the right panel.

Regards,
Roger 8)

---

