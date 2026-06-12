---
title: "ALT key not working properly"
date: 2021-06-21
forum: General Help
---

### Post by claus on 2021-06-21
Hi all,

right now, I''m having the problem that the ALT key in Blender is not working. I went to **Control Center > Keyboard**, but couldn't find the ALT key alone, only in combination with another key. I also can't use the ALT key in Photoshop CS2 (CrossOver Linux). What can I do to solve this issue?

TIA,

Claus

---

### Post by GhX6GZMB on 2021-06-21
What's it supposed to do? I've never heard of using the Akt key alone.

---

### Post by dragonfly41 on 2021-06-21
By coincidence I am studying hot keys in Blender.
There is a wide list of hot key commands. It is quite complicated to learn.


[LIST]
[*]Alt – When held while editing values, it applies the changes to all the selected items, including objects, bones and sequence-strips. It can be used for number fields and toggles.
[/LIST]

You could try **xev** in Ubuntu desktop to see if Alt key event is recognised.

Refer also here to change Blender key bindings .. if required ..

[https://docs.blender.org/manual/en/latest/editors/preferences/keymap.html](https://docs.blender.org/manual/en/latest/editors/preferences/keymap.html)

---

### Post by claus on 2021-06-21
> **ml9104 said:**
> What's it supposed to do? I've never heard of using the Alt key alone.

Sorry, in this case it's [Alt]+[Right-Click]. In Blender, it is there to select mesh loops.

Claus

---

### Post by claus on 2021-06-21
P. S.: By assigning [Left-Click] or [Shift]+[Left-Click] to mesh loops, I was able to circumvent the problem. Thanks to all who responded.

Claus

---

### Post by dragonfly41 on 2021-06-21
While continuing to learn Blender UI I have decided to build a desktop automation client, running in background. which converts instructions to generate/emulate hot key sequences.  There are simply too many hot key sequences to learn.

Meanwhile you might appreciate this example of integrating Wolfram Mathematica with Blender.

[https://community.wolfram.com/groups/-/m/t/2293492](https://community.wolfram.com/groups/-/m/t/2293492)

---

