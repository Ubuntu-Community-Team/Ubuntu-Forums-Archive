---
title: "[SOLVED] Firefox flash problem"
date: 2007-07-07
forum: General Help
---

### Post by NeoNecro on 2007-07-07
Hello,

I'm having a problem in firefox with the flash player plugin installed. Whenever I view a page with a flash animation on it my whole system freezes, sometimes I can still move my mouse around, but the system doesnt react on clicks. After a while it unfreezes, but then quickly freezes again.

I have this problem on my laptop only, I have a desktop computer with exactly the software and dont have those problems (it could be that my desktop has an older version of the flash plugin).

I'm using kubuntu 7.04 x86 on hp pavilion dv6000 with a geforce 7200 go card in it.

---

### Post by bettlebrox on 2007-07-07
Sounds like something else is using the sound card.

---

### Post by NeoNecro on 2007-07-07
> **bettlebrox said:**
> Sounds like something else is using the sound card.
I dont think it is the sound card, because sound is always working fine.

I've just disable the nvidia drivers and am now using the nv drivers and didnt had the problem. I think it has something to do with the hardware.

I had problems installing the nvidia drivers and needed to do a bios upgrade, it looks like there are still some problems. 

I sometimes also get a warning message saying: "disabling irq #7"

---

### Post by bettlebrox on 2007-07-07
In the past with a crappy soundcard I've have flash lockup the browser if it can't access the soundcard. 

I'd try the nvidia driver again and look in /var/log/Xorg.0.log for error messages and in ~/.xsession-errors .

Luck!

---

### Post by NeoNecro on 2007-07-10
After a lot of research I found that it is a problem when using ndiswrapper in combination with nvidia drivers. I found a lot of useful information on the following locations:
[LIST]
[*][http://bbs.archlinux.org/viewtopic.php?pid=262717](http://bbs.archlinux.org/viewtopic.php?pid=262717)
[*][https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28DV6000%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28DV6000%29)
[*][http://www.nvnews.net/vbulletin/showthread.php?t=94413](http://www.nvnews.net/vbulletin/showthread.php?t=94413)
[/LIST]

You need to use a 2.6.20 kernel or newer and boot it with the **pci=usepirqmask** parameter.
I don't need the noapic or any other parameters now.

I'm now using ndiswrapper and the nvidia drivers at the same time, and it is stable for most of the time. Sometimes when I watch flash movies it freezes for a short time, but it also unfreezes. It is not perfect, but I'm happy with it for the time. I gues most of these problems are because of all the new hardware in this laptop and will be solved over time.

---

### Post by NeoNecro on 2007-07-11
My previous solution only helps to get rid of the irq errors I get on my laptop.
To solve my problem I needed to install 100.14.09 driver, now it's working great.

---

