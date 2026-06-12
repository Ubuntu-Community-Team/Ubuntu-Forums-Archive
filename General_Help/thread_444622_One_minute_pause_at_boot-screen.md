---
title: "One minute pause at boot-screen"
date: 2007-05-15
forum: General Help
---

### Post by SirOracle on 2007-05-15
Hi
I use Ubuntu Feisty on a Dell Latitude D620 (Dual Core).

When I boot up my computer, the boot-process pause for about one minute when the progress-bar on the boot-splash are at about 30%.

Anyone know how I can fix this? Or help me find out what to do to find out what is causing this pause.

Thanks!!

---

### Post by iheartme on 2007-05-15
Maybe this thread will help out: [http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

Bootchart let's you see what's going on during boot, and you'll probably see what exactly is slowing things down.

---

### Post by SirOracle on 2007-05-15
Thanks for the reply, but I'm not sure how to read from this chart what could be wrong. Could you take a look please? I added the chart as an attachment.

---

### Post by iheartme on 2007-05-16
Sure, I'll have a look! I must warn you that I'm no expert either, so let's hope we can make some sense out of it :)

I'm going away in about 30 min so I can't look at it until tonight/tomorrow, but I'll install it on my machine and see what looks different!

Meanwhile, take a look at [http://www.bootchart.org/](http://www.bootchart.org/). Maybe they got some useful information on how to interpret the chart.

Edit: If you look at the samples on [http://www.bootchart.org/samples.html](http://www.bootchart.org/samples.html), you'll see that the networking bits in those charts are a LOT shorter than they are on yours. What happens if you disable networking on bootup?

---

### Post by kaamos on 2007-05-16
You can also press ctrl+alt+F1 or ctrl+alt+F9 (Fsomething anyway) during boot to see the messages.

---

### Post by iheartme on 2007-05-17
> **kaamos said:**
> You can also press ctrl+alt+F1 or ctrl+alt+F9 (Fsomething anyway) during boot to see the messages.

Or you could just remove the "quiet" and/or "splash" part from grub. Don't know why I didn't think if of that in the first place :)

---

### Post by SirOracle on 2007-05-18
I pressed CTRL+ALT+F1, and I was able to see what was going on. And I could see that the pause was at "Configuring netowork interfaces".

It's one gigabit ethernet card and one wlan-card on this computer. I dont use the ethernet-port, only the wlan card.

Any idea?

---

### Post by SirOracle on 2007-05-20
I followed the suggestion on this post:
[http://ubuntuforums.org/showthread.php?p=2419738#post2419738](http://ubuntuforums.org/showthread.php?p=2419738#post2419738)
That worked for me. It boots quick and everything seems to work fine.

Thanks for the help!

---

