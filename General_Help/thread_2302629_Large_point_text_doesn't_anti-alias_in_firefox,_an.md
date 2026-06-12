---
title: "Large point text doesn't anti-alias in firefox, and only in firefox."
date: 2015-11-11
forum: General Help
---

### Post by Brendan_Leason on 2015-11-11
I can't really wrap my head around the problem I'm having here. It doesn't make much sense. Text anti-aliases fine in almost every instance, with the single exception of very large point font in Firefox, which doesn't anti-alias at all. I have no idea why. This is most noticeable in Wikipedia, where none of the headers anti-alias. I've tried changing the fonts several times, I've tried changing the anti-aliasing settings to every conceivable option, I changed the LCD hinting setting, I rebooted the computer multiple times, I tried Firefox in Xfce4 (xubuntu), Unity, and in Cinnamon, all to no avail. The problem does not occur in Chromium, and did not occur just a few hours ago. The only variable that has changed is that I have installed Cinnamon, but I don't understand how that could cause this.

Actually, it just occurred to me that I also enabled bitmapped fonts, but as above I don't see how that could cause this.

I took some screenshots. They aren't the best, I really should've picked a page with more large text, but you can make out that in the Firefox version, the title is very much a jaggy mess, and not in the Chromium version.

[http://imgur.com/a/VNAYq](http://imgur.com/a/VNAYq)

---

### Post by Brendan_Leason on 2015-11-12
Well, I've discovered that it doesn't just affect large text. Random bits of normal sized text are also suffering this problem, and it's more than a little annoying.

---

### Post by Brendan_Leason on 2015-11-12
UPDATE

Since evidently either nobody knew the answer or nobody had the energy to shout the answer, it seems that it was, in fact, RTFM. Apparently enabling bitmapped fonts systemwide causes Firefox to throw a tantrum and decide, for no reason, to use them in completely inappropriate places. The answer was to block them again and add exceptions to the fonts I wanted enabled. This has fixed the problem.

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

