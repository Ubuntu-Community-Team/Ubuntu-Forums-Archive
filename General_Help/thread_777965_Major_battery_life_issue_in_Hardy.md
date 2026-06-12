---
title: "Major battery life issue in Hardy"
date: 2008-05-01
forum: General Help
---

### Post by Jugney on 2008-05-01
I've been running Ubuntu since Gutsy on an HP dv6000 with AMD Turion dual core processor, 2GB RAM, and a 120GB hard drive with 4GB of that being swap. When I switched from Vista to Ubuntu I noticed a decrease in battery life. But what's happened after doing a clean install of Hardy is just crazy. My battery only lasts 30 minutes.

I recently learned about laptop_mode, so I've enabled that. After unplugging the AC to test it out, it has gone from 100% to 70% in just under 10 minutes. 

I recently changed my power management settings so that the laptop never sleeps on its own, but I doubt that would make such a major difference.

Any ideas what the heck is going on???

Jugney

---

### Post by honeydew on 2008-05-01
powertop may provide you with a bit more information. 

```
sudo apt-get install powertop
```

it will tell you which programs are causing the most processor wakeups.. IE sucking power.. it could also be something lowerlevel.. like a driver handling some hardware incorrectly.

---

### Post by Jugney on 2008-05-01
Thanks for the suggestion - I tried it out and found that "extra timer interrupt" was usually in the 35% - 50% range for reasons for wakeups. Any ideas what that means?

I'm still suspicious since I only saw this issue with the new install of Hardy.

Has anyone else had this problem after going to Hardy Heron?

Jugney

---

### Post by Bubba64 on 2008-05-01
I read a posting that said it takes the new program a little time to correctly read the battery. I have noticed no difference in my laptop battery usage during the time I had Hardy.

---

### Post by Steve- on 2008-05-03
With Gusty I had up to **5 hours** battery life, but with hardy I get just **2 hours**.

2 hours is pointless for a laptop, so I'm at the state of going back to Gusty. Hopefully we can get some good dev support behind this and solve the problem, it seems to be quite widespread!

---

### Post by Jugney on 2008-05-15
I'm still having problems with this issue. Does anyone have any experience like this where they can offer wisdom?

I have replaced powernowd with cpudyn, I have set cpu frequency scaling to powersave mode, I have laptop_mode enabled. I've used powertop and reported the results above (i.e. extra_timer_interrupt comes up higher than anything else when I'm not using the mouse or keyboard. But I don't know if that's something I can work with or not)

What actually happens is that the battery drains by jumps of 10% every few minutes. Looking at the battery icon in the gnome upper panel shows, say 50% when I place the mouse over it. When I click on it, it often shows a reading 11 percents below that - 39%. And they always go up or down by ten.

When I booted Vista in VirtualBox this morning my laptop didn't even last 10 minutes! 

Any ideas? It's an HP dv6308nr with dual AMD Turion 64 X2 TL-50s.

---

### Post by Jugney on 2008-05-15
UPDATE: I think I've found the problem! 

I just clicked on the battery icon to get more information. Get this:

It says the Capacity is 5% (Poor)
Last full charge was 4.0Wh and the design charge is 75.5 Wh.

Both times I installed Ubuntu, whether Gutsy or Hardy Heron, I got a popup on the first bootup saying the battery was not running or charging to capacity. When I installed Gutsy the computer was about 6 months old (it would get about an hour and a half to a charge) and now it's about 9 months old.

What can I do about this? 

Jugney

---

### Post by Steve- on 2008-05-15
I checked out my battery information also, and the last full charge wattage was much lower than the design charge. 

I'm going to give it a full charge and drain now and will report the statistics to you.

Is there anyway we can get this information in Gutsy? I could then pop my old HDD back in and give a direct comparison of the loss of performance.

---

### Post by niharsm on 2008-05-15
I too had a similar problem. I started getting error that battery is charging to 67% of designed capacity after shifting to Ubuntu.

---

### Post by Steve- on 2008-05-15
After fully charging the battery, I unplugged the cord and these are the stats it gave me:

> Product: DELLUD2606
Percentage Charge: 99%
Vendor: Sanyo
Technology: Lithium ion
Model: DELLUD2606
Capacity: 59% (Poor)
Current Charge: 56.8 Wh
Last full charge: 56.8 Wh
Design charge: 95.5 Wh
Charge rate: 33.0 W

Whilst I know batteries deteriorate, there is no chance it was this bad before I installed Hardy.

I sense a major flaw in the power management code! I'm happy to run more tests if someone can give some developer feedback.

---

### Post by badfish591 on 2008-05-15
huh, thats wierd, i get about a half-hour more battery time out of hardy than my vista partition out of the box

---

### Post by Jugney on 2008-05-15
Well, I clicked on my battery icon again and saw that the design charge changed - to 69.5 Wh from 75.5 Wh. I don't know where Ubuntu is getting the design charge figure from, but obviously is should stay the same. So maybe it is misreading that. 

Nonetheless, my very real problem that the battery only lasts 15-20 minutes on a full charge is still here. Perhaps this is an HP specific issue? Doesn't slow down much when wireless is turned off, either.

Is there anyone who knows the reason for this problem who can contribute to this discussion???

---

### Post by fragos on 2008-05-16
I just did a clean install of 8.04 on a Dell Inspiron 1420n. I see no difference in battery life from the 7.10 I was running.

---

### Post by Jugney on 2008-05-16
Thank you for the reply. I understand this is not an issue that everyone running Hardy Heron has. For the sake of keeping this thread clean and useful to people who might visit it in the future, can I ask that people only post if they have a substantive addition or insight to add to this issue?

Jugney

---

### Post by fragos on 2008-05-16
You could try cleaning the battery contacts. Also double check the notorious battery consumers -- back light, WiFi, PCMCIA/Express card, USB connected devices using the power to charge themselves. Given your experience is different, the question to ask may be what is different about my install and hardware from those without problems. Don't totaly dismiss the posibility that the battery is at fault. There are stores that specialize in batteries that may be able to test your battery for you.

---

### Post by hansel_nz on 2008-05-16
I have the same issue with my HP dv2000. It's 9 months old and the battery only charges up to 38% This dramatic change seemed to coincide with the installation of Hardy... however I'm not sure that it isn't just the battery being a faulty piece of sh*t. Of course HP are refusing to replace it because I've voided the warranty by installing another OS...

I'm taking it up with the local retailer because what they are trying to do to me is actually against the law in New Zealand. But ANYWAY, I'll let you know.

Cheers 

Hansel

---

### Post by Steve- on 2008-05-18
> **fragos said:**
> You could try cleaning the battery contacts. Also double check the notorious battery consumers -- back light, WiFi, PCMCIA/Express card, USB connected devices using the power to charge themselves. Given your experience is different, the question to ask may be what is different about my install and hardware from those without problems. Don't totaly dismiss the posibility that the battery is at fault. There are stores that specialize in batteries that may be able to test your battery for you.


Its highly unlikely that my battery gave up right as I installed 8.04, replacing my 7.10.
If you have a look at the battery stats (click the icon in your system tray, then click Laptop Battery), what Product and Vendor is your battery? Maybe a certain brand is at fault...

---

### Post by sdennie on 2008-05-18
The information that the battery popup displays comes directly from the BIOS.  You should be able to see the same info with:

```

cat /proc/acpi/battery/*/info

```

I don't think there is anything in Hardy that could cause a battery to lose it's maximum charge so it really does sound like your battery is either faulty or as someone else suggested, the contacts are dirty.

---

### Post by fragos on 2008-05-18
> **Steve- said:**
> Its highly unlikely that my battery gave up right as I installed 8.04, replacing my 7.10.
If you have a look at the battery stats (click the icon in your system tray, then click Laptop Battery), what Product and Vendor is your battery? Maybe a certain brand is at fault...

Gnome doesn't seem to provide that information. I tried some command line and couldn't come up with information. I do have the optional 9 cell battery.

---

### Post by fragos on 2008-05-18
Using vor's CLI I can now answer Steve-'s question.

FT0927 sn#2015 Panasonic

---

### Post by esteckis on 2008-05-18
I stopped using Hardy on my Dell 6400 Laptop.

When I run windows xp with speedswitch and safeXP (disables a lot of windows junk)I am able to get 5 hours with my 9 cell battery.

On Hardy, I only get 3 1/2 hours on a full charge. And that is with the backlight set at a very dim level to boot.

---

### Post by Klayy on 2008-06-18
I'm also having problems with battery life. In Vista I can get up to 3 hours on powersave and about 1:35 on high performance with wifi turned on and music in the background.
In hardy i always get 1:10 (or close to that) no matter what CPU policy I have. 
I manually set both cores to 229MHz and I can feel that they ARE at 229, cause everything is so damn slow. But the funny thing is that it doesn't change the remaining time estimate at all and the core temperature rises by 4-5 degrees celsius!

---

