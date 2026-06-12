---
title: "Laptop still &quot;thinking&quot; after shutdown"
date: 2008-04-05
forum: General Help
---

### Post by RedPandaFox on 2008-04-05
Hey, I am going to re-install Ubuntu on my Eee PC 4Gb surf, I had 7.10 and everything worked fine (with the exclusion of drivers which may be the problem with this) but whenever I shut down the laptop, all processes would end, and the laptop turn off, but the light which shows that it is still turned on is still on. I can hold down the power button and kill it but I was wondering if;
A) I could edit the shutdown sequence to kill all power usage after shutdown without effecting restarting it. or
B) Find drivers for my Intel mobile chipset for with the lan, wireless, sound, etc drivers made for Ubuntu? or maby even the default OS (darling linux) having drivers that might work on my Ubuntu (I will be installing the 8.04 beta if all goes well with 8.04 on my main pc) 

My other Eee PC (my girlfriends) is running well on XP with the XP drivers.


If anyone is interested also I am modifying the EeePC's with touch screens, bigger SSD's and ram.

Any suggestions for drivers or kill process?

---

### Post by warp99 on 2008-04-05
Very simple. Open a terminal and do the following:

```
echo "rmmod snd-hda-intel" | sudo tee -a /etc/default/halt
```

You don't need to reinstall Ubuntu. All of the drivers that are currently on your system will still be there since many of the drivers are already compiled into the kernel while others are included as kernel modules, restricted modules, additional modules, and so 

If you need additional help go the forums or the wiki at eeeuser.com. They have a complete section on Ubuntu.

BTW typing this from a Eee PC 4G, so welcome to the tribe.

---

### Post by s3a on 2008-04-06
sudo poweroff

---

