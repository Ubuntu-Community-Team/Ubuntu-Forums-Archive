---
title: "Hardware Information in Hardy?"
date: 2008-04-26
forum: General Help
---

### Post by bakaeigo on 2008-04-26
In Gutsy, there was something called "Hardware Information" under Preferences. Where did that go in Hardy?

---

### Post by Toxicity999 on 2008-04-26
Though I don't see this with a quick look either. What specifically are you trying to figure out with the tool? Maybe we could help you figure that out in the interim.

---

### Post by bakaeigo on 2008-04-26
I'm trying to identify my motherboard.

---

### Post by ibuclaw on 2008-04-26
I believe that the application that you are looking for is called "hardinfo"

It's in the repository:
```
 sudo apt-get install hardinfo
```

And there's another great app is call "**hwinfo**" too. Though it is a terminal based app and may prove to be too much jargon to take in at once.
But, if you are interested, you can sudo apt-get install it too.

Once you've finished installing hardinfo, a new item shall appear in your preferences menu.

Mine is named "**System Profiler**", though you can rename it by right-clicking on the menu tab and selecting "Edit Menu"

Regards
Iain

---

### Post by ibuclaw on 2008-04-26
> **bakaeigo said:**
> I'm trying to identify my motherboard.

You can identify your motherboard by opening up your case and looking inside.
There should be an identifiable name code printed onto it.

Unless you have a Laptop, then I'd advice against it unless you know what you're doing...;)

Also, you can find out when you boot up your computer.

Go into BIOS (usually a key such as Delete or F8 or F1 that gets you in). It also tells your what motherboard you have there too.

Regards
Iain

---

### Post by bakaeigo on 2008-04-26
> **tinivole said:**
> I believe that the application that you are looking for is called "hardinfo"

It's in the repository:
```
 sudo apt-get install hardinfo
```

And there's another great app is call "**hwinfo**" too. Though it is a terminal based app and may prove to be too much jargon to take in at once.
But, if you are interested, you can sudo apt-get install it too.

Once you've finished installing hardinfo, a new item shall appear in your preferences menu.

Mine is named "**System Profiler**", though you can rename it by right-clicking on the menu tab and selecting "Edit Menu"

Regards
Iain

That's exactly what I'm looking for. Unfortunately, It doesn't show the motherboard model as I thought it would. Is there any way to do this without opening up my computer?

---

### Post by ibuclaw on 2008-04-26
> **tinivole said:**
> 
Also, you can find out when you boot up your computer.

Go into BIOS (usually a key such as Delete or F8 or F1 that gets you in). It also tells your what motherboard you have there too.

Regards
Iain

Your PC should display a BIOS splash screen at boot-up.
It disappears rather quickly, but you should be able to read the line that tells you how to access the BIOS.

---

### Post by bakaeigo on 2008-04-26
Going into the BIOS options did the trick.
:) Happily running an updated BIOS now

---

