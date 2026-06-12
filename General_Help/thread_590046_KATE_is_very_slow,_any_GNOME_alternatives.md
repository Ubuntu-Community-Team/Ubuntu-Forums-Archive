---
title: "KATE is very slow, any GNOME alternatives?"
date: 2007-10-24
forum: General Help
---

### Post by svivian on 2007-10-24
I installed the KDE Advanced Text Editor, since I've used it on other distros and loved it. However it seems quite slow - it's taking several seconds to load up, and if I run it from the terminal I get these errors:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Any ideas?

Also a minor annoyance: since it's a KDE app it doesn't fit in very well on GNOME. In particular, the Open/Save dialog is very different. Is it possible to change the interface look? Or, can anyone recommend a similar full-featured text editor for GNOME?

I'm running Ubuntu Feisty, BTW.

---

### Post by kellemes on 2007-10-24
gedit

---

### Post by Yarbo on 2007-10-24
I've you're using standard Ubuntu then "gedit" seems to be the way to go, thats what i've been using.

---

### Post by sci-fi guy on 2007-10-24
A quick check of Add/Remove reveals these options:
GVim
SciTE (for programming)
Scribes
Mousepad
medit
Leafpad

as well as the standard Gedit and Kate.

---

### Post by svivian on 2007-10-24
Well I never used to like gedit, but I've played with it for a bit and it's not too bad now. Maybe I just missed the config/plugins before.

Some things I'm missing:
- remember the files I has open last time (i.e. sessions)
- syntax highlighting for multiple sections, eg PHP/HTML - currently with PHP mode I can set all HTML to be one single colour, but can't apply the same highlighting that a HTML file on its own gets.
- change line highlight colour

Are any of these possible?

---

### Post by sci-fi guy on 2007-10-25
In Gedit, go to Veiw>>Highlight Mode for syntax highlighting.

---

### Post by svivian on 2007-10-25
> **sci-fi guy said:**
> In Gedit, go to Veiw>>Highlight Mode for syntax highlighting.
Doesn't work, I can only choose one at a time.

After a look at Wikipedia though I've discovered Bluefish which has most of the stuff I like :)

---

### Post by Neostar on 2007-10-25
Yea Bluefish is great for creating websites. But give GVim a try it's also very good, the interface can be a bit strange but very workable.

---

