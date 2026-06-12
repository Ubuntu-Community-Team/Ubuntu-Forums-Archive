---
title: "drivers stopped loading on boot"
date: 2008-04-14
forum: General Help
---

### Post by Arrowx7 on 2008-04-14
Hello,
I tried compiling a new kernel 2.6.24, but it wasn't stable in regards to my wireless drivers.
I removed it (did dpkg -i)
Now I booted to my first original kernel, and none of the drivers are loading properly:
My wlan0 disappeared, touchpad stopped working, all th hotkeys (such as Fn+sleep) stopped working, and on boot it asks me to identify my video card (after each boot).  If someone can help me diagnose the problem, would appreciate it.

Laptop: Lenovo Thinkpad T61
Wireless card: Intel Pro Wifi 4965AGN
uname -a:
Linux sts700 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Running Gutsy

I can load the drivers manually with modprobe, but none load without this:
Here is an example with my wireless

```

asal@sts700:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

asal@sts700:~$ lspci | grep 4965
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

asal@sts700:~$ modprobe -l | grep 4965
/lib/modules/2.6.22-14-generic/updates/drivers/net/wireless/iwlwifi/iwl4965.ko

sudo modprobe -r iwl4965

sudo modprobe iwl4965

iwconfig --> AND THERE IT WAS


```

wlan0 showed up and started working now...very weird.  I think i just re-inserted the wireless driver module into the kernel.  When I reboot, I have to do it again to get wireless to work. But what about my touchpad, graphics, etc..  Is there a way to reinsert all drivers?
I don't even know driver names for those things.  Any way to have them load on boot again?

Any suggestions would be awesome! thanks,

AR

---

### Post by Arrowx7 on 2008-04-15
Come on guys, i don't believe that nobody knows how to make the drivers load at boot time (modprobe).  Can anyone point me in the right direction please?

Thanks a lot,
AR

---

### Post by game_plan on 2008-04-15
I have to agree with you, I've been working on getting wireless to load automatically on boot for a while. But no threads helpful threads. I've heard people say add this to your /etc/network/interfaces file, but didn't work for me, hope you have better results.
[CODE]
auto wlan0
iface wlan0 inet dhcp

---

### Post by Arrowx7 on 2008-04-20
anyone please?

---

### Post by jkeyes0 on 2008-04-21
If you're wanting to modprobe something on boot, add it to /etc/modules

---

