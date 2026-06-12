---
title: "Opera gone mad?"
date: 2006-11-07
forum: General Help
---

### Post by fractalvibes on 2006-11-07
I've been using Opera for the past couple of months on Kubuntu with great success - really a nice browser.  For some reason, he past few days Opera refuses to recognize the intended formatting, background color, etc.  basically every site looks like the Drudge Report now...can't say that I or anyone else has monkeyed with any settings.

The only thing I can think of is that I have tried using Adept recently instead of Synaptic to check for updates most everyday, but I assume both are simply front ends to Apt so it should not matter? i.e same package list and all?

Anyone have a similar experience?  Could I have downloaded an update that wonked up Opera?  I tried uninstalling and reloaded the package from the Oper a site to no avail - same results.

Screen shots below of the main page of Ubuntu site.

thanks,

fv

---

### Post by Dual Cortex on 2006-11-07
> **fractalvibes said:**
> I've been using Opera for the past couple of months on Kubuntu with great success - really a nice browser.  For some reason, he past few days Opera refuses to recognize the intended formatting, background color, etc.  basically every site looks like the Drudge Report now...can't say that I or anyone else has monkeyed with any settings.

The only thing I can think of is that I have tried using Adept recently instead of Synaptic to check for updates most everyday, but I assume both are simply front ends to Apt so it should not matter? i.e same package list and all?

Anyone have a similar experience?  Could I have downloaded an update that wonked up Opera?  I tried uninstalling and reloaded the package from the Oper a site to no avail - same results.

Screen shots below of the main page of Ubuntu site.

thanks,

fv


roflmfao!!!
Drudge report... very true!

Anyway, are you in the 'author mode' (or something similar)?
Press the magnifying glass next to the search textbox. One of the buttons that appear in the bar should read User Mode or Author mode (again not sure of their names). Click them and see if anything happens.

---

### Post by kuja on 2006-11-07
Well, one thing that might be worth trying is this:

1. Close out all instances of opera
2. in a terminal:
```

sudo rm -rf ~/.opera

```

To delete all of your settings. Might work for you, assuming that something really is messed up.

---

### Post by fractalvibes on 2006-11-07
Damn!  Who the hell clicked the "author mode"???!!!!  If I wanted to see it in "author mode" I would just view the source.  Damn.  What is the purpose of this "author mode"?  Opera folks have some sort of Drudge fetish?

Anyway - thanks a bunch - that took care of it.  When Opera first wonked out  I felt like I was on a Windows machine....


Thanks!

fv

---

