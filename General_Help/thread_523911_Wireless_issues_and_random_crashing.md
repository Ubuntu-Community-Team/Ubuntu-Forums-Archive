---
title: "Wireless issues and random crashing"
date: 2007-08-12
forum: General Help
---

### Post by DrIdiot on 2007-08-12
I just switched from Gentoo Linux to Ubuntu and I'm having some issues.

Firstly, I cannot connect to the internet.  The networks are listed and have good signal strength, but when I try to connect, it won't.  On gentoo I did not have this problem (to connet to the network I would type /etc/init.d/net.ra0 start as root), so I don't think it's a problem with the router.


Secondly, my computer crashes a lot.  For example, sometimes when I try to open the network configuration, it won't open, and the applets on the panel would freeze up, but the mouse would still move and the only thing I can do to fix this is restart my computer.

Does anyone know what's causing these issues?

Thanks,
-Harrison

---

### Post by gobbles414 on 2007-08-12
Hmm... interesting! Can you please provide more detailed specs for your system? I am most curious about the: brand of computer, amount of RAM (and is it shared with graphics memory), processor type/speed, hard drive capacity. Also, how is your wireless configured: are you using a card, is your wifi built-in, are you trying to connect to a network that is secured with a method other than WEP?

---

### Post by DrIdiot on 2007-08-12
yep.  i built the computer about 6 months ago.  it's run gentoo for 6 months until a dependency break totally screwed over my system and i got frustrated and decided to install ubuntu.

the specs are:
intel core 2 duo 2.0 ghz cpu
1 gb ram
gfx card: nvidia geforce 7600gt
300 gbhard drive, partitioned as such:
50 gb windowsxp, 100 mb /boot, 2 gb swap, 100 gb / and teh rest /home

i am using a wireless PCI card that has an external antennae.  my network is not secured by WEP but it does have a MAC filter.  however, my MAC address is on the router list, and i was able to connet to it before from gentoo.

---

### Post by gobbles414 on 2007-08-12
Have you looked in System --> Administration --> Restricted Drivers Manager? The wifi card in my laptop doesn't work unless the restricted driver is activated. While the restricted driver for my wifi was activated automatically by Ubuntu, my 3D graphics were not. So maybe your wifi driver still needs to be loaded?

---

### Post by DrIdiot on 2007-08-12
hm, ill try that when i get home, but it seems like the hardware is working.  i recall seeing that it was using the rt61 module (which is correct) and also it can detect roaming network and their signal strengths but when i try to actually connet it just times out.

---

### Post by whoami1988 on 2007-08-12
I was having this problem, and my current temporary solution is to restart dbus instead of reboot. I found it browsing the forums, and it works for me when my connection gets disconnected after suspend. 

> sudo /etc/init.d/dbus restart

---

### Post by DrIdiot on 2007-08-12
i looked under restricted drivers and there's only my nvidia driver.  oddly, when i click to enable it, it asks me whtehr i want to, and if i say yes, then nothing happens.  it's stll not installed.  does it require a workign interne connection?

also, my network card driver is open source. (rt61)

---

### Post by DrIdiot on 2007-08-12
Also, I can't restart dbus because my keyboard stops responding.

---

### Post by DrIdiot on 2007-08-12
I fixed the itnernet problem by doing manual configuration instead of roaming.  I had to restart for this to take effect though, because dbus crashed again when I changed the config.  after the internet worked it resolved most of the issues I had.

---

### Post by gobbles414 on 2007-08-12
Dridiot,

On my laptop, I actually wasn't able to download the 3D acceleration drivers from the Restricted Drivers Manager (although it was listed there). I went to System --> Preferences --> Desktop Effects and that forced a download of the appropriate video drivers.

BTW, congratulations on solving your internet issue! :KS

---

