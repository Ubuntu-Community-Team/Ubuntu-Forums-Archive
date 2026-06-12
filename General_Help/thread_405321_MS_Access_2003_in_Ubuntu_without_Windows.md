---
title: "MS Access 2003 in Ubuntu without Windows"
date: 2007-04-09
forum: General Help
---

### Post by Stonecougar on 2007-04-09
So, I'm in the process of trying to cut Windows out of my personal computing life altogether. The trouble is that I'm going to school for a degree as a database administrator, and I'm taking a class this quarter about MS Access 2003. Thusly, I need to have Access 2003, specifically, available to me at home. If OpenOffice would cover it, I'd go with that, but alas... 

Anyway, here's the question... I've seen that people can get Access 2003 working in Ubuntu by reading it off their Windows partition. Well, my desktop doesn't have a Windows partition anymore. Is there any way I can get Access to run smoothly in Ubuntu without having to install one? Right now, that's the only thing that's keeping my XP Pro installation on my laptop. If Ubuntu can be made to run it on its own, then I'll happily snip that tenuous little string.

---

### Post by rufius on 2007-04-09
You won't be able to run Access 2003 natively on your linux installation. The best you'll get is running it via Wine if you're not willing to install Windows in a VM and use it that way. I wouldn't recommend using the development version of Wine but rather using [link=http://www.codeweavers.com/products/cxoffice/]CodeWeaver's Crossover Office[/link]. Its a commercial version of Wine which is designed specifically to work with Office. Its a bit costly, but in my past (brief) experiences with it it seemed pretty good.

---

### Post by Stonecougar on 2007-04-09
Hm. Crap. I figured I'd have to use Wine or something... but as a starving student, I can't afford to go shell out for Crossover. Guess I'll just have to keep Windows around on my laptop... *Sigh*

---

### Post by rufius on 2007-04-09
Well you can use Wine, its just that Crossover Office is a simpler solution. If you want to use Access 2003 badly enough you could probably get it running. How new is your laptop? If its pretty recent (ie 2006 or later) then I would say try out running Windows XP in kvm (kernel-based virtual machine). Here's more info:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by Stonecougar on 2007-04-09
The laptop is a brand new Alienware M5550 that I just got like two or three weeks ago. I spent my entire spring break fighting with Windows on three machines, so I want to ditch it completely as soon as possible. I'll give that a shot, and report back with my (hopefully) success story!

---

