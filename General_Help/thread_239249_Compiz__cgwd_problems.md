---
title: "Compiz / cgwd problems"
date: 2006-08-19
forum: General Help
---

### Post by Orunitia on 2006-08-19
So, tonight, my title bars randomly have stripes in them on every transparent theme. It is really starting to piss me off, so anyone have any ideas what's going on?

[http://img83.imageshack.us/img83/8031/screenshotho4.png](http://img83.imageshack.us/img83/8031/screenshotho4.png)

And yes, I've reinstalled cgwd AND compiz twice and this crap is still going on.

---

### Post by hopstah on 2006-08-19
are you sure the theme isn't supposed to be like that?  it's so minor, i don't think i would have even noticed it.  to be honest with you, i wouldn't let it get to me.

---

### Post by TheRingmaster on 2006-08-19
I don't notice anything out of the ordinary with that theme.

---

### Post by Orunitia on 2006-08-19
Look harder, there are black stripes throughout the titlebar. And yes, since I've been using the theme for the past two days, I know it's not supposed to be like that. Not trying to be rude, but someone who has used compiz and these themes please help me instead.

And I have ocd over these types of things, so please please don't tell me it's too small to worry about.

---

### Post by TheRingmaster on 2006-08-19
I too use compiz/xgl. What is the themes name?

---

### Post by spockrock on 2006-08-19
it looks like you are running the reflection plugin.  see if you have it enabled in your plugins in gconf.  apps>compiz>general>options>active_plugins

reflection will add that to your you windows or decorations.

---

### Post by hopstah on 2006-08-19
> **Orunitia said:**
> Not trying to be rude, but someone who has used compiz and these themes please help me instead.i have compiz and am using a theme almost identical to that.  i had to look really hard before i could even see that there was some color fluctuation in the title bar
> And I have ocd over these types of things, so please please don't tell me it's too small to worry about.i was just expressing my opinion and telling you what i would do.  some things are just too small to lose any sleep over.  if something was functionally wrong with your computer, that's one thing.  but seeing as it's compiz/xgl, you should *expect* things to go wrong, as it's still in early beta.

---

### Post by Orunitia on 2006-08-19
> **spockrock said:**
> it looks like you are running the reflection plugin.  see if you have it enabled in your plugins in gconf.  apps>compiz>general>options>active_plugins

reflection will add that to your you windows or decorations.
Disabled it and it's still there. :(

> i was just expressing my opinion and telling you what i would do.  some things are just too small to lose any sleep over.  if something was functionally wrong with your computer, that's one thing.  but seeing as it's compiz/xgl, you should *expect* things to go wrong, as it's still in early beta.

Oh I know, I expect things to break. I was just saying that even small things like this get on my nerves.

---

### Post by spockrock on 2006-08-19
after disabling it did you try to restarting compiz??

also what engine is your theme using??

---

### Post by Orunitia on 2006-08-19
> **spockrock said:**
> after disabling it did you try to restarting compiz??

also what engine is your theme using??

Was at work or I would of responded earlier. I just restarted and it fixed it. All I did earlier was ctrl+alt+backspace. I feel like a fool. Thanks for the simple suggestion that fixed it.

---

### Post by spockrock on 2006-08-19
glad to hear it, you could also restart compiz in terminal with

```
compiz --replace
```

or use compiz-start.py script as well.


Also if you wanted you can still use reflection and change the reflection map.

---

