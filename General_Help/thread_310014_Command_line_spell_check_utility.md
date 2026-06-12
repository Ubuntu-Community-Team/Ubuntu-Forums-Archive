---
title: "Command line spell check utility?"
date: 2006-11-30
forum: General Help
---

### Post by rajan on 2006-11-30
Hi, I'm pretty impatient and I don't like to open up a Open Office document every time I want to spell check a single word. I know dictionary.com does this too, but I can open a terminal way faster than a browser. Is there a utility that I could use on the command line to spell check? I couldn't find one and I think it may be the case that none exists, so how would i interface the spell check program in something like firefox or open office with a terminal?

Thanks for any help,

Rajan

---

### Post by kylevan on 2006-11-30
there's a dictionary panel applet for GNOME.  alternatively, Deskbar integrates the dictionary with other functionality.

---

### Post by Arisna on 2006-11-30
`aspell' is a command line spell checking utility, though a dictionary sounds like more of what you want.  kylevan's suggestion is good, though if you're curious about a command line solution, look into wordnet.

---

### Post by rajan on 2006-12-01
great! thanks guys... I'll be checking these things out over the weekend. if i find an easy way to interface the terminal with a commonly available spell checking program, i'll repost on this thread.

thanks again

---

### Post by Blazeix on 2007-09-04
I know this is an older post, but I found this thread while googling, and I figured I'd post my solution here.

I use vim for my text editing. To spell check from inside vim you can use aspell. In command mode, type:
```

:w !aspell -a

```
This will scan through your document, find misspelled words, and suggest corrections.
If you use Ubuntu, aspell is most likely already installed on your machine.

---

