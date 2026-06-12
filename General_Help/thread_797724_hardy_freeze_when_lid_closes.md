---
title: "hardy freeze when lid closes"
date: 2008-05-17
forum: General Help
---

### Post by nkobel003 on 2008-05-17
Hello Everyone,

Whenever I close my laptop lid or go away from the computer for a while, my screen gets very glitchy, unrecognizable actually, and will not respond to anything but CTRL+ALT+BACKSPACE. Is there a way to prevent this from happening? It never did this in 7.10, but it does it in 8.04.

Thanks,

Nick

---

### Post by strabes on 2008-05-17
What are your power settings? I suppose you could just take a screenshot of the gnome-power-preferences window. I suspect this has to do with your computer trying to suspend after a specified period of time.

---

### Post by nkobel003 on 2008-05-17
Here is a picture of the power management... 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=70490&stc=1&d=1211055539[/IMG]

(I don't know if it's trying to suspend because it just says "blank screen." Also, if it is trying to suspend, how do I let it do that without messing up my display / session? I was able to shut the lid or walk away in 7.10, so you'd think I'd be able to now, maybe...

Thanks again

---

### Post by nkobel003 on 2008-05-17
Ahh, I solved my own problem...

I changed the "When laptop lid is closed" option to Do Nothing instead of Blank Screen.  It works perfectly now. Thanks for showing me that function (although I swore I messed with it before, lol).

Nick

---

### Post by kentcb on 2008-05-17
I have this same problem, but I'd really like to know how I can get suspension / hibernation to work. It'd be nice to be saving power when the laptop lid is closed.

Is this a known issue with Hardy? I'm new to linux altogether so not sure whether suspend/hibernate is something that normally works.

Thanks,
Kent

---

### Post by nkobel003 on 2008-05-17
For me, suspension and hibernation both work, it's just the "Blank Screen" option that doesn't work. Open a terminal and run:
```
gnome-power-preferences
```
What are your preferences and such?

---

### Post by mardawi on 2008-05-17
> **kentcb said:**
> I have this same problem, but I'd really like to know how I can get suspension / hibernation to work. It'd be nice to be saving power when the laptop lid is closed.

Is this a known issue with Hardy? I'm new to linux altogether so not sure whether suspend/hibernate is something that normally works.

Thanks,
Kent

There are some users experiencing problems with suspend and hibernate with ubuntu, specially older versions. You can look up for solutions by searching the forum for your laptop type and series. Good luck!

---

