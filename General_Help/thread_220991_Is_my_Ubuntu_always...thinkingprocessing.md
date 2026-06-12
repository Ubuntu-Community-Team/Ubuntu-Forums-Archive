---
title: "Is my Ubuntu always...thinking/processing?"
date: 2006-07-22
forum: General Help
---

### Post by Burgresso on 2006-07-22
I noticed on my new install that my Ubuntu always sounds like it is thinking - you know, that sound computers make when they are processing information - its hard to explain, but I have a hunch many people will understand what I mean.

Is this normal? I've got 2g of ram with a AMD 64, 2.6g processor with a huge HD. Everything is new; its a new build.

SHould I be worried or concerned, or is this normal?

gracias

burgresso

---

### Post by aysiu on 2006-07-22
You can see what's going on.

Paste this command in the terminal: ```
top
```

---

### Post by jordilin on 2006-07-22
Well, you can do a top, or go to System->Administration->System monitor. The sound you hear, most probably is the cpu or graphics card fan. It's normal, not worry. With your hardware your cpu should be in normal conditions around the 0% of usage.

---

### Post by Burgresso on 2006-07-22
Cool, thanks a lot. I'm going to assume its normal unless the PC starts acting strange. : )

I appreciate the responses.

---

### Post by hellmet on 2006-07-22
personally, I feel a bit different.
I feel it actually processes text rather than strings
of 0s and 1s.
It mite sound hilarious but I feel windows processes somthing
else, and Ubuntu (Linux in general) processes text.
this is because..ever since I started/used Linux all I cud see
was the lines of text at start or shut down.
I somehow got used to it..and  thus the impression.
now don't L you AO

---

### Post by hellmet on 2006-07-22
And I somehow like that feeling a lot!! he he

---

### Post by RJARRRPCGP on 2006-07-22
> **Burgresso said:**
> I noticed on my new install that my Ubuntu always sounds like it is thinking - you know, that sound computers make when they are processing information - its hard to explain, but I have a hunch many people will understand what I mean.

Is this normal? I've got 2g of ram with a AMD 64, 2.6g processor with a huge HD. Everything is new; its a new build.

SHould I be worried or concerned, or is this normal?

gracias

burgresso

That's the HDD you're hearing. If you're worried about it, check the RAM and swapfile usage.

---

### Post by Burgresso on 2006-07-22
Thanks RJARRRPCGP. Are the defaults often not the best setup for RAM or swap? How do check it out?

---

### Post by Burgresso on 2006-07-24
By HDD you mean hard drive disk, right?

---

### Post by bobosity on 2006-07-24
In Gnome right click on the top panel and choose 'add to panel'. Then choose system monitor. Right click on the monitor and select preferences. Add everything: memory, swap, load etc.

Now you can glance at the panel anytime and get an idea of what's going on.

---

