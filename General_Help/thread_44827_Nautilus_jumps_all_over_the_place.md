---
title: "Nautilus jumps all over the place"
date: 2005-06-27
forum: General Help
---

### Post by twistymcgee on 2005-06-27
When I am looking at a folder in nautilus then select one of it's subfolders, the window jumps to another random location on the screen...like some sort of sick game I have to chase this thing all over the screen  :) 

I think I know why it's doing it.  It is opening a new window when I click on the subfolder and placing it randomly and closing the current one.  At least that's my guess.

Anyway, is there anyway to make it stop?  I just want it to load the new folder in the current window and stay where it's at.

---

### Post by twistymcgee on 2005-06-27
I Just realized I probably should have put this in the desktop forum.  Can someone move it for me?

---

### Post by Tyr_7BE on 2005-06-27
You've just been exposed to Ubuntu Spatial Mode.  Annoying, isn't it?

To turn off, go Applications->System Tools->Configuration Editor.

Once that's open, find /->apps->nautilus->preferences and check the "no-ubuntu-spatial" option.

From what I understand, the next rev of Ubu will contain an option in the nautilus preferences tab to disable this.

---

### Post by WiLLiE on 2005-06-28
[QUOTE=Tyr_7BE]From what I understand, the next rev of Ubu will contain an option in the nautilus preferences tab to disable this.[/QUOTE]

Next rev?

It's already there. just goto: (In Nautilus menys)
(roughly translated from swedish)

Edit-->Properties
Second tab "Behaviour"
tick "Always open in ...."

Close and start Nautilus again..
There.. no more spatial  :smile:

---

### Post by ow50 on 2005-06-28
There's 3 modes:
Ubuntu spatial
Gnome spatial
browser

Switching between spatial and browser can be done in the Nautilus preferences dialog. Switching between the two spatials can be done only with gconf (Configuration editor).

---

### Post by WiLLiE on 2005-06-28
Yeah, I know.
But this is what the man says:

[QUOTE=twistymcgee]
......
I just want it to load the new folder in the current window and stay where it's at.
[/QUOTE]

---

### Post by twistymcgee on 2005-07-01
Perfect.  Thanks guys.  I did it in the nautilus behaviour dialog.

---

