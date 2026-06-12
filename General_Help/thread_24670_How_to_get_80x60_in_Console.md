---
title: "How to get 80x60 in Console"
date: 2005-04-07
forum: General Help
---

### Post by Wyld on 2005-04-07
Howdy all,

I'm trying to find a way to obtain (and keep) 80x60 text in console.  My aim is to have my consoles running bitchx and admin whilst using xwindows for .. well .. xwindowing (games, etc).

I've tried setting it via grub but it's wiped back to 80x24 during boot.

I've tried setting it using consolechar but flipping to xwindows and back breaks it.

Any ideas on a perminant solution here?

---

### Post by Nis on 2005-04-07
[QUOTE=Wyld]Howdy all,

I'm trying to find a way to obtain (and keep) 80x60 text in console.  My aim is to have my consoles running bitchx and admin whilst using xwindows for .. well .. xwindowing (games, etc).

I've tried setting it via grub but it's wiped back to 80x24 during boot.

I've tried setting it using consolechar but flipping to xwindows and back breaks it.

Any ideas on a perminant solution here?[/QUOTE]
 You can try appending a vga=792 line (or similar) to your kernel line in your grup config.  This sets up a framebuffer on boot so the virtual terminal will have a lot more space.  One of the settings should give you something close to 80x60 (the above, however, gives me 1024x768).

---

