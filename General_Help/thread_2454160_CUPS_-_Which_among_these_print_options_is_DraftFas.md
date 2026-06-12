---
title: "CUPS - Which among these print options is Draft/Fast Mode?"
date: 2020-11-23
forum: General Help
---

### Post by ardouronerous on 2020-11-23
I've installed my printer, Canon iP2700 on Xubuntu 20.04. The printer's driver is Canon iP2700 series - CUPS+Gutenprint v5.3.3, and these are the print options offered to me and I don't understand them, which among these is Draft/Fast Mode?

[ATTACH=CONFIG]287446[/ATTACH]

---

### Post by ardouronerous on 2020-11-26
Bump

---

### Post by Autodave on 2020-11-26
I would assume that it is one of the 300 x 300 modes.  "Mono" I assuming to be black and white, so probably 300 x 300 Mono.

---

### Post by ajgreeny on 2020-11-26
Looks as if you have the option to use 300x300 dpi with the black ink only or colour ink only (this will generally give a dark grey/brownish print, not true black) or using both inks, which is the default.

I must say, I have never seen the print modes described in this way before, but perhaps I just haven't looked!

---

### Post by ardouronerous on 2020-11-26
Thanks for the replies guys.
Unfortunately, 300x300 dpi isn't draft/fast mode. Just found the PPD file, and it doesn't contain any draft/fast mode feature. Looks like I'm stuck with printing Windows XP on VM.

Here's the PPD in question: [https://paste.ubuntu.com/p/kDR96cn7WS/](https://paste.ubuntu.com/p/kDR96cn7WS/)

Do you think there's a way to add draft mode to the PPD file?

---

