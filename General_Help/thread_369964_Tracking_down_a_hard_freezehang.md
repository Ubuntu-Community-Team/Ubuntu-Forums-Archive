---
title: "Tracking down a hard freeze/hang"
date: 2007-02-25
forum: General Help
---

### Post by alphaxxn on 2007-02-25
Just got done installing Ubuntu on another computer of mine, and at first had a problem with installation. Pretty common on these forums, it kept hanging at around 50ish percent complete. I uninstalled my wireless LAN card to try to see if that'd work -- because I saw that it was going haywire/active during installation. After my first try after uninstallation of the wlan card it installed perfectly. I reinstalled and have been tryin to get my network up. It went up no problem but for whatever reason with the regular ath_pci drivers that ubuntu uses it seemed to make the computer want to hang, or atleast so I thought. I switched to the NDISWrapper drivers for the atheros chipset I have and the problem is still identical. Now on to the actual symptoms/stats/etc.

The problem is that every time I download anything bigger than a website (say the ubuntu updater for example.. ) it hard-locks as if it were a kernel panic, and very rarely it'll lock during bootup. 

Now, the questions. I would love to know how to track down freezes and hangs like this. How can I access the system logging or error logging so I can see what exactly it's tryin to do when it hard locks? Also are these symptoms atypical of a wireless lan card problem or something more sinister?

Thanks a lot guys.

-Sam


Oh, PS

1.2GHZ AMD Athlon,  256megs SDRAM
80gig WD , Onboard Soyo Audio/USB
Savage Video


Thanks a lot.

---

### Post by shaunbarlow on 2007-04-06
Hi all,
I'm a newbie to linux, got most stuff happenin by myself, and pleased to say I love Ubuntu. 
I've got far less technical know how than alphaxxn, but I'm having a similar problem with a wireless. I've installed my Netgear WG111v2 wireless dongle (yes it is actually the v2) using NDISWrapper and the Win98 driver from the Netgear site. 
Just as described above when there's more than a little network traffic the whole computer locks up; no keyboard, mouse, hard drive activity, on screen things stop and I've got to hit the reset button.
I can reproduce this reliably by opening evolution and surfing youtube at the same time.

I'm narrowing it down to something related to the wireless cos I've been surfing pretty hard on my new 512K connection using a wired connection to my router for a day with no problems at all.

Please help, it's a pain in the ... having to run a chain of modems and routers across my house to reach the computer.

Cheers,
Shaun

---

