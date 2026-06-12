---
title: "Printing from Firefox 3"
date: 2008-06-11
forum: General Help
---

### Post by smotsie on 2008-06-11
Hi guys,

Since upgrading to FF3 I have lost "sensible" printing. In FF2 when I clicked File | print I got a nice dialog where I could choose which printer, alter it's setup to portrait, duplex etc, and then choose which pages to print. Now in FF3 I get a print progress box and then the whole document prints on a default printer. No choice, no dialog. FF3 seems to be more stable than FF2 (which regularly crashed in GMail) but I would even go back to the crashes to have the choice of what to print, where.

Has anyone else got this problem, and has anyone found out how to fix it? (It DOES NOT happen in any other app)

FF 3.0 updated today running on Kubuntu 8.04 with all latest updates

Cheers

Smotsie

---

### Post by Jobbe on 2008-06-12
Hey, I had the very same error. I checked about:config and it seems that one of the settings print.always_print_silent and print.postscript.cups.enabled was responsible. Both were set to false and I reset them both before checking the effect, thus I can't tell exactly which one did the trick, but I strongly suspect it was the latter.

Hope that helps.

Oh, btw, the way I did this might not be the most healthy way. Try to check those setting's effects before changing them... :D

---

### Post by smotsie on 2008-06-12
Yaaayyyy!!!! Many thanks for that - it was the first setting print.always_print_silent which was set to true, now set to false and I get my printing dialogue back!
:)
This really should be the default, with a check box in the dialogue saying "don't show this dialogue, just print" and a way in the preferences to set it back.

---

