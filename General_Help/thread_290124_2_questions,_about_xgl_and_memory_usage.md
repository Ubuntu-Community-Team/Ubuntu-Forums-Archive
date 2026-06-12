---
title: "2 questions, about xgl and memory usage"
date: 2006-10-31
forum: General Help
---

### Post by rabid emu on 2006-10-31
Ok I have 2 questions that may or may not be related (I don't actually know).
I'm on Edgy btw.

1st question: I installed Xgl and Beryl for gnome, along with the fglrx driver for my ati card.  This worked out great, until I saw that xgl apparently overwrites xorg.  Now I can't really install other Desktop environments like KDE or Enlightenment because it says there's a conflict with x.  Is it possible for me to restore the stock xorg that came with Edgy, install these other desktop environments, then somehow restore the eye-candy (be it xgl or Aiglx)?  And on a side note will KDE support the eye candy as well?

2nd question: If I have ubuntu running for a few hours, the amount of memory that is being used as cache keeps rising.  Right now it's at 73% of my total memory, but it's been up to 85% before.  When I used to run FC5 I never noticed this extensive memory usage. Is there a way to just clear the cache without rebooting?  Or is it not that big of a deal at all?  it is possible, also, that beryl/xgl is eating up some memory but I have no idea about that.

---

### Post by tribaal on 2006-10-31
Can't really help you for the first question, but for an in-depth explanation of linux memory management, check the first link in my sig out.
Actually, it is a design choice: unused RAM just sits there being a waste of ressources, so instead linux fills it up with disk cache (RAM being of course much faster to access than disks). Whenever your system needs more RAM (for an application), the application has priority over the cache, so the cache data gets overwritten and performances aren't hampered in any way.

Hope this answers your question :)

- trib'

---

### Post by rabid emu on 2006-10-31
It does answer my second question, thanks.  I guess the memory monitor I was using in Fedora just didn't show the amount of memory being used as cache.

---

### Post by rabid emu on 2006-10-31
bump

---

