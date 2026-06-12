---
title: "slow boot"
date: 2007-03-19
forum: General Help
---

### Post by Mba7eth on 2007-03-19
hi all... i used to have a very slow boot up process. I've tried many things to speed it up, but didn't successed. But i have noticed something weird yesterday. I have booted my laptop in recovery mode and i have noticed from messages that are displayed during the boot process that every thing goes fine until it reaches the network configuration section. it take there around a minute and a half.... :confused: 
Any suggestion to speed the bootup process . 
My specification : dell 640m laptop, 2.0GHZ core2, 1GB ram, 256RM 945intel chipset video card

---

### Post by floke on 2007-03-19
First make a backup

sudo cp /etc/network/interfaces /etc/network/interfaces_backup

Then 

sudo nano /etc/network/interfaces

And hash out everything except for

auto lo
iface lo inet loopback

If this buggers anything up then try unhashing some of the stuff you've commented out - eg unhash eth0 or whatever it is your network is on (might be a good idea to check this before you start).

I had a very long delay at this point and the above just whistles through it all now - the entire boot is now less than the original delay time.

Hope it helps

---

### Post by Henry Rayker on 2007-03-19
I had a similar issue with my laptop anytime I would boot without my wireless device plugged in (or when the network wasn't around). I just hit ctrl-C to skip that portion of the boot process. If this is a desktop, though, Steve's solution should bring some sort of success.

---

### Post by floke on 2007-03-19
Well it works on my laptop too. Couldn't be bother to use ctrl-c all the time :)

---

