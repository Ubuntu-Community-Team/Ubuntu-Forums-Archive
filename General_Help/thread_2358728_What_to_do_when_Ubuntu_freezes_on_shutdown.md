---
title: "What to do when Ubuntu freezes on shutdown?"
date: 2017-04-16
forum: General Help
---

### Post by finksu on 2017-04-16
What is the right thing to do when Ubuntu freezes on shutdown? No, not how to fix it. I had freeze today on shutdown. I've had Ubuntu for 6 months but I broke it 2 times, so currently my installation is about 1 month old. I use version 16.10. I shut my computer down and when the animation was on for about 4 seconds, HDD stopped spinning and animation froze. What to do when that happens? I did NOT install anything or update anything.
I have external HDD with Ubuntu I use every day. 
Specs:
My laptop has Intel Celeron N2840 @ 2.17 GHz processor
Ubuntu GNOME 16.10 
Windows 8.1 on computer's HDD
Edit:
It was just one-time freeze, so I don't have to fix it any way. But thanks for your answers!

---

### Post by RobGoss on 2017-04-16
Hello and welcome to the forum, What are the specs for your machine give as much information as you can so users my try to trouble shoot your issue

---

### Post by finksu on 2017-04-17
I want to know what to do at the exact moment it happens. Not, how to fix it (yet).

---

### Post by dragonfly41 on 2017-04-17
Try REISUB SysReq key sequence ... used for such occasions ...

Search &#8220;REISUB&#8221; in this forum or look here for a summary ...

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

Look for SysRq key on your keyboard (on mine it is on F11 key).

So press both Alt + F11 and hold down    [COLOR=#ff0000]*(see later correction below to use Print Scrn key not F11 in my case)*[/COLOR]

followed by key sequence ...

R
E
I
S
U
B

Regarding fixing, there is a relevant thread here ...

[https://ubuntuforums.org/showthread.php?t=2354865&highlight=REISUB](https://ubuntuforums.org/showthread.php?t=2354865&highlight=REISUB)

This suggests adding 

```
acpi=force
```
into grub ..
```
GRUB_CMDLINE_LINUX_DEFAULT=quiet splash acpi=force
```

You can do this manually or there is a useful package Grub Customizer
which you might find under System Tools > Administration

**[EDIT]**

Correction to above .. it is some time since I have used this "get out of jail" card so I tried it. It did not work.

I read this article ... [https://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/](https://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/)

and found that although I have **SysRq** printed on my Dell F11 key the actual key which works is **Prnt Scrn**.

And Alt + Print Scrn needed to be held down together followed slowly by R .. E .. I .. S .. U .. B

---

### Post by sonicwind on 2017-04-17
I found it isn't necessary to hold down both the Alt + Print Scrn keys at the same time.

Holding down Alt followed by Print Scrn .. R .. E .. I .. S .. U  .. B worked. One less finger needed :)

Also, you can use R E I S U O to turn the computer off rather than reboot it.

---

