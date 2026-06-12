---
title: "gnome-terminal function keys"
date: 2007-03-23
forum: General Help
---

### Post by dmik on 2007-03-23
After upgrading to Feisty, gnome-terminal started to generate "wrong" sequences when pressing Shift/Alt/Ctrl-F1..F4 keys, and some other. In particular, it generates:
```

            Shift     Alt       Ctrl
F1          \EO1;2P   \EO1;3P   \EO1;5P
F2          \EO1;2Q   \EO1;3Q   \EO1;5Q
F3          \EO1;2R   \EO1;3R   \EO1;5R
F4          \EO1;2S   \EO1;3S   \EO1;5S

```
while it should:
```

            Shift     Alt       Ctrl
F1          \EO2P     \EO3P     \EO5P
F2          \EO2Q     \EO3Q     \EO5Q
F3          \EO2R     \EO3R     \EO5R
F4          \EO2S     \EO3S     \EO5S

```
according to the output of the **infocmp** command (TERM is default **xterm** here). The second variant of sequences is exactly what happens in the Edgy installation on another computer.

It looks like **1;** gets added to the middle of the sequence for these function keys and also in the middle of sequences for combinations like Shift-Up/Down/Left/Right.

Is there a way to configure/fix this behavior? It is quite annoying because I cannot use, say, Shift-F4 to create a new file in Midnight commander, or Shift+Arrows to select text any more.

Btw, the **xterm** application both in Edgy and Feisty generates sequences from the first table (i.e. with **1;** inserted), but I found how to fix it by editing xterm resources (/etc/X11/app-defaults/XTerm-color). Is there something similar for gnome-terminal?

---

### Post by iv0 on 2008-06-29
Hello,

I have exactly the same annoying problem. I have searched for a solution, but didn't find anything, except this bug report, solution suggested there is not exactly perfect...

[https://bugs.launchpad.net/gnome-terminal/+bug/96676](https://bugs.launchpad.net/gnome-terminal/+bug/96676)

I use Hardy 64bit in Czech language.

---

