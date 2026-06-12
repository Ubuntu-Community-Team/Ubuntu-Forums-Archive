---
title: "the borders &amp; frames to my windows disappeared"
date: 2008-05-09
forum: General Help
---

### Post by Th3Professor on 2008-05-09
How do I get them back?

I tried a fresh reboot, though they're still gone.

---

### Post by Perfect Storm on 2008-05-09
What did you do in first place that they gone missing?

---

### Post by Th3Professor on 2008-05-09
I have absolutely no idea. :confused:

---

### Post by Perfect Storm on 2008-05-09
Did you tried enabled graphic driver? Or tried enable Desktop enhancements? Installed/updated something?

---

### Post by Th3Professor on 2008-05-09
Did you tried enabled graphic driver?
Nope.

Or tried enable Desktop enhancements?
Nope. (Though compiz + the cube-stuff/etc. was already installed/enabled.)

Installed/updated something?
Nope. (Though I do let the system do auto-updates.)

---

### Post by Perfect Storm on 2008-05-09
So let me get this straight - You installed a clean Ubuntu and it wasn't there?

Ok.

Try this;
```
metacity --replace
```

---

### Post by Th3Professor on 2008-05-09
It's actually Ubuntu Studio.

They were there originally.

I did set up conky to load at boot, so maybe...

Or maybe... something with compiz and/or "advanced desktop effects settings".

?

I'll go ahead and try "metacity --replace" in either case.

EDIT:
Okay, metacity --replace put them back... though it disabled my fancy compiz features... going to try to re-enable the cube/etc.

EDIT 2:
Ah ha! Got it... it was "reflection" in the advanced desktop effects settings.
When I enabled "reflection" it made the frames/borders disappear.
When I disabled it, they came back. :)

---

