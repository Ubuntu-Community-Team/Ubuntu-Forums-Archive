---
title: "dead keys not working"
date: 2008-05-18
forum: General Help
---

### Post by jon.reeve on 2008-05-18
I've been trying to use the Canadian Multilingual Keyboard to type French, but the dead keys won't work, thereby prohibiting me from typing any character with a circumflex or umlaut, which is quickly becoming a major problem. I can remember dead keys working in Gutsy, but for some reason now that I have Hardy they aren't working. 

Typing any dead key doesn't have any effect at all, and when I kill SCIM it prints the symbol itself (ie the circumflex or umlaut on its own, without a letter underneath) rather than acting as a dead key.  I also tried enabling a compose key, but to no avail with or without. I ran 

```
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

and got this output: 
```

 layouts = [us,ca	multix]
 model = 
 options = [Compose key	compose:menu,grp	grp:alts_toggle]
 overrideSettings = true
```

Any ideas?

---

### Post by jon.reeve on 2008-06-04
Anyone?

---

