---
title: "Can I turn off the hint balloons/msg boxes/hints/whatever?"
date: 2007-05-12
forum: General Help
---

### Post by 3rods on 2007-05-12
Is there anyway to turn off those yellow boxes that pop up when you float over anything (i.e. program list in main menu, tab titles in firefox, ect.)? I'm running beryl if there is a setting to disable them in there. 

I don't remember them being that annoying before; maybe my cpu/gpu was never fast enough to make them pop up so quickly.

---

### Post by cknoblock on 2007-05-12
Hello 3rods,

If I am understanding your question correctly, open gconf-editor from a terminal and go to apps->panel->global and uncheck tooltips_enabled.

-chris

---

### Post by 3rods on 2007-05-12
Sweet heck! Tool tips, damn, that's what they're called. Either way, thanks for saving my sanity.

---

### Post by merlinus on 2007-05-13
I followed these instructions, but still get the so-called tool tips and balloons.  :( 

I even logged out and back in again.

-merlin

---

### Post by OrangeCrate on 2007-11-23
Found this thread while searching for something else this this morning. I add this post in case someone finds this thread searching for an answer to this.

The above gconf suggestion turns off the Ubuntu tool tips. The Firefox tool tips are turned off by typing "about:config" in the address box and hitting enter. Then find the "browser.chrome.toolbar_tips" item and double-click to turn it's value to false.

This takes care of all of the "yellow boxes". And yes, they are annoying.

---

### Post by B0whunt3r on 2008-01-24
> **cknoblock said:**
> Hello 3rods,

If I am understanding your question correctly, open gconf-editor from a terminal and go to apps->panel->global and uncheck tooltips_enabled.

-chris

this works for the 'applications' system 'places' but what about the clock?

I still get the annoying click to view your appointments and tasks.

---

### Post by p_quarles on 2008-01-24
If I remember right, the clock/calendar is actually part of Evolution, and not part of the Gnome panel. Open that up, and play with the tooltip settings in there.

---

