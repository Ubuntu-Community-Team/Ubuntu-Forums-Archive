---
title: "Shouldn't ubuntu start up even faster?"
date: 2008-03-01
forum: General Help
---

### Post by Redrazor39 on 2008-03-01
I have a fairly nice laptop. It's a VAIO VGN-SZ430N with

Intel Core 2 Duo 2GHZ
2GB DDR2 RAM
NVIDIA GEFORCE GO 7400
335 MB VIDEO RAM


and it can take up to a full minute to start up, almost as slow *as Windows Vista.* Ubuntu should be MUCH faster, especially on a laptop with fairly solid specs like this. Is it because my laptop is "too new" (even though it's almost a year old, something should've improved by now) and that the hardware isn't being used fully and properly or does ubuntu just suck?

Can I expect improvements in Hardy?

I was hoping ubuntu could compete with and beat Macintosh computers. This is my way of saying "ha" to my mac-using friends.

Is there any way to make ubuntu start up really fast, or can I expect improvements in Hardy?

And what are some programs/etc. that make ubuntu REALLY cool, better than macs?


and btw, Suspend doesn't work on my laptop. It just goes black screen with blinking lights and I just have to reset my entire system.

---

### Post by scragar on 2008-03-01
I'm current using a 2.2Ghz Dualcore, and can say that it's not the processing power that slows ubuntu down during boot, it's the input/output wait from the HD(try running it again in a VirtualBox where you can monitor CPU usage and HD usage if you don't belive me).

I can't say anything else though, since I'm primarily happy with my boot experience.

---

### Post by pointone on 2008-03-01
You could use bootchart to see where the boot process is spending the most time, then tweak your system accordingly.

---

### Post by Rocket2DMn on 2008-03-01
One of the best ways to speed up boot is to reprofile from GRUB, it's really easy, check it out: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
Here is another guide for tweaking boot: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Joeb454 on 2008-03-01
I think it's an issue with Gutsy (7.10). I've seen a lot of people claiming to have a faster boot time with Fiesty (7.04) and Hardy (8.04) :)

Hope this helps

---

### Post by Redrazor39 on 2008-03-01
It's not a huge issue for me, but it's noticeable. It's not like I can impress anyone with ubuntu boot times, which I really wanted to do. Should I just wait until Hardy?

---

### Post by Redrazor39 on 2008-04-25
I will upgrade to Hardy in a week or so and I hope the boot will be fixed.

---

### Post by Rocket2DMn on 2008-04-25
Cool, don't forget to profile the boot sequence after you do the upgrade since your boot order will have changed.  It's the easiest and most effective way to speed up boot.

---

### Post by Redrazor39 on 2008-04-25
> **Rocket2DMn said:**
> Cool, don't forget to profile the boot sequence after you do the upgrade since your boot order will have changed.  It's the easiest and most effective way to speed up boot.

And how exactly do you do that?


sorry for being so nooby-- I'm a bit new at this stuff

---

### Post by Rocket2DMn on 2008-04-25
In the first link I posted above (way back when): [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

