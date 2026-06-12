---
title: "Console refresh rate"
date: 2007-09-22
forum: General Help
---

### Post by Lem on 2007-09-22
I'm using a formac monitor on dvi. Works fine, except for the text console, which I can't seem to make appear. I've tried adding different vga options to grub, but the best I've got is a garbled version of the x session.

I think this is a refresh rate issue - it seems the formac only supports a vertical refresh of 60hz, which might explain why I can't see my bios screen on this screen either (works fine with a vga socket screen).

Can i change the refresh rate for the text console?

---

### Post by dcstar on 2007-09-22
> **Lem said:**
> I'm using a formac monitor on dvi. Works fine, except for the text console, which I can't seem to make appear. I've tried adding different vga options to grub, but the best I've got is a garbled version of the x session.

I think this is a refresh rate issue - it seems the formac only supports a vertical refresh of 60hz, which might explain why I can't see my bios screen on this screen either (works fine with a vga socket screen).

Can i change the refresh rate for the text console?

Try adding video=vesafb:800x600-16@60 to the Grub boot line.

---

