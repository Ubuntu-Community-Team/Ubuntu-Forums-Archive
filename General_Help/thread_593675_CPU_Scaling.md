---
title: "CPU Scaling"
date: 2007-10-27
forum: General Help
---

### Post by Imsati on 2007-10-27
Well, I only have a few days left on my RMA window for my current motherboard, so I thought I'd seek help one last time for a strange problem I'm having. I am currently using an Abit IL9 Pro board with a Pentium D 940 CPU. The CPU is able to run at either 2.4Gh or 3.2Gh, thanks to EIST. When I use XP, I see that it does in fact cut back it's speed when idle, as shown by running CPU-Z to verify. However, Ubuntu 7.04 and 7.10 will not scale it back. I added the Frequency Monitor applet to my taskbar and got the message saying CPU scaling wasn't supported. Every time I would load up Ubuntu, I would get that same message, and I eventually just removed the applet from the taskbar.

Does anyone have any ideas as to what I can do? The IL9 Pro is a pretty decent board, I'm coming to find out, but it's BIOS is very limited, and it has next to zero OCing options, so I cannot manually play with CPU settings. Could this be a chipset problem? -Maybe Ubuntu doesn't like something programmed on the board itself? My RMA runs out on the 30th, and I really want CPU scaling to work with Ubuntu, as I'm trying to use it more and more and only booting to XP when necessary.

FWIW, my chipsets are 945P and ICH7. A Gigabyte board with either a P31 or P35 chipset was recommended to me if this one will not work. Any ideas?

Thanks :)

---

### Post by p_quarles on 2007-10-27
Have you tried cpudyn? 

```
sudo apt-get install cpudyn
```
The frequency monitor applet isn't a very powerful program, as far as I know, but I've had success using this.

---

### Post by Imsati on 2007-10-27
Well, I just installed that and Powernowd or whatever was auto-uninstalled. I put two instances of the Frequency Monitor on the taskbar so I could see both cores. One was at 2.4 and the other at 3.2.

So I open up a Terminal and this is what I got:

jason@JasonU:~$ cpudynd
cpudynd version 1.0 Copyright: Ricardo Galli <gallir@uib.es>
cpudynd: CPU frequency control disabled
Error: Nothing to do, exiting

jason@JasonU:~$ 

Which again makes me believe it's a MoBo problem controlled through BIOS. But since I can't change and CPU settings in my BIOS...I'm back at square one :(

I'm running the latest version for my BIOS. Is it possible to flash a new BIOS over it? Meaning, can I use a completely different company's BIOS? Instead of AMI maybe use Phoenix?

Heading out for a Halloween party in a bit, but I'll check back later tonight when I get home.

---

### Post by Imsati on 2007-10-28
Anyone have any ideas? 2 days left to RMA it.

---

### Post by Imsati on 2007-10-29
RMA needs to be filed by the end of today. Anyone?

I really like this board, but want it to work perfectly! If no advice, I'll have to replace it.

---

