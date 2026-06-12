---
title: "HELP!!! Ubuntu 18.04 - black screen, no boot, no grub, no USB-booting"
date: 2018-10-15
forum: General Help
---

### Post by Constantinopolitan on 2018-10-15
Dear all,

I am new here; I normally ask my questions in another forum but lost my access to it with the access to my computer. When trying today to install driver etc. for my new Wacom Cintiq drawing board, something went terribly wrong. I suspect it has something to do with xserver-xorg.

The system advised me to restart my computer in order to enable the new software to start. I shut down and restarted the computer, and what happened? The Ubuntu Logo came on the screen, it disappeared, the screen went black and afterwards only a space sign (_) appeared. I inserted a USB stick to boot from there, which did not work naturally, but finally came through when pressing F6. When looking for my files to save them on an external disk, I found that the folder was empty (luckily, this covers only work from the last days).

For some reason I shut down the computer again, I simply cannot recall why, but it was a very bad idea. Upon restarting, nothing worked anymore. Pressing Shift does not bring me to the GRUB menu, and F6 makes the Xubuntu logo appear and flicker frantically until I release F6. I read somewhere that pressing Escape might help, but upon doing that, I find:

```
[B]Minimal BASH like line editing is supported. For the first word,  TAB lists possible command completions. anywhere else TAB lists  possible device or file completions.
grub>
grub>
grub>
(and some 25 more lines like that)
[/B]
```

What can I do to recover my computer and, hopefully, my files?

I need to submit a project urgently end of this week, and now I am paralysed (this type of things always arrives when least needed)!

My heartfelt thanks to anyone who has a good idea to help me!

Best regards,

Eva

---

### Post by dragonfly41 on 2018-10-15
It is easier for me to point you to earlier troubleshooting of same symptoms.

This is one thread suggesting installing boot-repair (on your LiveUSB) and applying boot-repair via LiveUSB.

[https://ubuntuforums.org/showthread.php?t=2351583](https://ubuntuforums.org/showthread.php?t=2351583)

---

