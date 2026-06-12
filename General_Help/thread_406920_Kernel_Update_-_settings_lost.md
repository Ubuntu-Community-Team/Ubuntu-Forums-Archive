---
title: "Kernel Update - settings lost?"
date: 2007-04-11
forum: General Help
---

### Post by adamr on 2007-04-11
After today's kernel update, I've noticed more settings changed than I expected. I'm still very new to Ubuntu really, but when I saw the update details as it was installing, I caught a glimpse of it doing something with grub, and sure enough my booting has changed a little (I had verbose output on during startup), but that's nothing major. 

I was surprised to find that *some* of my networking settings had changed though. My manual wireless card details were still in place (DHCP just refuses to work for me, no idea why), but when I tried to get online I was having problems. I could get to my router's page no problem so knew it was a DNS issue, and sure enough, my DNS settings were reset to default.

Is this to be expected during a kernel update, or maybe it was something else that got updated at the same time? It just seems really odd to lose some of the settings and not others. Is there a good way to back them up? I'm not sure which file holds the configuration.

Thanks in advance.

---

### Post by esaym on 2007-04-12
No it shouldn't change anything

---

### Post by spankymasterc on 2007-04-12
yeah it changed my settings to i just 

sudo gedit /boot/grub/menu.lst 

and changed my settings back

::cheers::

---

