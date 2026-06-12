---
title: "Vaio laptop shuts down unexpectedly 16.04"
date: 2018-01-19
forum: General Help
---

### Post by moralesj10 on 2018-01-19
Hello 

I have a fresh install of 16.04 using the xfce DE
The laptop is a Vaio VPCCW17FX
The laptop suddenly shuts down and its been doing this about every hour or so. Ive been using this laptop for hours before but suddenly today it keeps turning off. I checked the sensors and the temps are all good. I am able to turn it back on right after it shuts down and it acts normally. 

If you need any more info, let me know

---

### Post by moralesj10 on 2018-01-21
bump

---

### Post by cruzer001 on 2018-01-21
Please post your system specs.

```
inxi -b
```

---

### Post by moralesj10 on 2018-01-22
System:    Host: pc Kernel: 4.13.0-26-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   System: Sony (portable) product: VPCCW17FX v: C6036GH9
           Mobo: Sony model: VAIO
           Bios: American Megatrends v: R0190Y5 date: 09/22/2009
CPU:       Dual core Intel Core2 Duo T6600 (-MCP-) speed/max: 1200/2200 MHz
Graphics:  Card: NVIDIA GT218M [GeForce G210M]
           Display Server: X.Org 1.19.5 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.94hz
           GLX Renderer: NVA8 GLX Version: 3.0 Mesa 17.2.4
Network:   Card-1: Marvell 88E8057 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
Drives:    HDD Total Size: 500.1GB (3.3% used)
Info:      Processes: 195 Uptime: 3 min Memory: 989.6/3912.7MB
           Client: Shell (bash) inxi: 2.2.35

---

### Post by cruzer001 on 2018-01-22
One thing I see that may or may not have to due with your problem.
> 
Display Server: X.Org 1.19.5 drivers: nouveau (unloaded: fbdev,vesa)

Your running the generic (nouveau) driver.  I think you should upgrade. here's how:

[https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+install+graphic+driver+ubuntu+16.04&ie=utf-8&oe=utf-8#kpvalbx=1](https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+install+graphic+driver+ubuntu+16.04&ie=utf-8&oe=utf-8#kpvalbx=1)

Also check "Using processor microcode firmware" (under Unknown).   There may be some updates coming your way.  Has to do with this:
[https://ubuntuforums.org/showthread.php?t=2381801&page=3&p=13733146#post13733146](https://ubuntuforums.org/showthread.php?t=2381801&page=3&p=13733146#post13733146)

I have a couple of other ideas, but try this first.

---

### Post by moralesj10 on 2018-01-22
Thank you so much for helping me
I've done what you said and updated.
I checked the updates with the code on the second link you provided and it looks up to date
I'll be back if this issue persists, but if not again, I really appreciate it

---

### Post by moralesj10 on 2018-01-23
> **cruzer001 said:**
> I have a couple of other ideas, but try this first.

Yesterday it worked fine but Ive had it on for about 30m and it turned off by itself again. What else do you think it could be?

---

### Post by Hadaka on 2018-01-23
Hi,perhaps ?
"System:    Host: pc Kernel: 4.13.0-26-generic x86_64 (64 bit)"

There are major problems with that kernel, as noted here..
[https://askubuntu.com/questions/9958.../995948#995948]("https://askubuntu.com/questions/995819/touchpad-gestures-and-holding-keys-does-not-work/995948#995948")
Boot the computer while holding down the shift key.
choose kernel 4.13.0-25 and see if there any improvements.
Thanks.

---

### Post by moralesj10 on 2018-01-23
Hello and thanks for you help as well

Ive done what you said but dont see that option on my screen, I only see
Ubuntu, with Linux 4.13.0-31-generic 
Ubuntu, with Linux 4.13.0-31-generic (upstart)
Ubuntu, with Linux 4.13.0-31-generic (recovery mode)
Ubuntu, with Linux 4.13.0-26-generic 
Ubuntu, with Linux 4.13.0-26-generic (upstart)
Ubuntu, with Linux 4.13.0-26-generic (recovery mode)
Ubuntu, with Linux 4.13.0-28-generic
Ubuntu, with Linux 4.13.0-28-generic (upstart)
Ubuntu, with Linux 4.13.0-28-generic (recovery mode)
Ubuntu, with Linux 4.4.0-112-generic
Ubuntu, with Linux 4.4.0-112-generic (upstart)
Ubuntu, with Linux 4.4.0-112-generic (recovery mode)
Ubuntu, with Linux 4.4.0-109-generic
Ubuntu, with Linux 4.4.0-109-generic (upstart)
Ubuntu, with Linux 4.4.0-109-generic (recovery mode)

I have already made the updates cruzer001 suggested so these are the updated system specs

System:    Host: pc Kernel: 4.13.0-31-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   System: Sony (portable) product: VPCCW17FX v: C6036GH9
           Mobo: Sony model: VAIO
           Bios: American Megatrends v: R0190Y5 date: 09/22/2009
CPU:       Dual core Intel Core2 Duo T6600 (-MCP-) speed/max: 1200/2200 MHz
Graphics:  Card: NVIDIA GT218M [GeForce G210M]
           Display Server: X.Org 1.19.5 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1366x768@59.94hz
           GLX Renderer: GeForce G210M/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 340.104
Network:   Card-1: Marvell 88E8057 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
Drives:    HDD Total Size: 500.1GB (3.9% used)
Info:      Processes: 190 Uptime: 8 min Memory: 1149.6/3912.8MB
           Client: Shell (bash) inxi: 2.2.35

---

### Post by cruzer001 on 2018-01-23
> **moralesj10 said:**
> Yesterday it worked fine but Ive had it on for about 30m and it turned off by itself again. What else do you think it could be?

Exactly whay Hadaka said :)  The kernel

For some reason your box is not updating your kernel, plus you have way too many.

Try booting the "Ubuntu, with Linux 4.13.0-31-generic" kernel.

And since you have it you can also try "Ubuntu, with Linux 4.4.0-112-generic".

We can do some kernel cleanup afterward.

---

### Post by moralesj10 on 2018-01-25
> **cruzer001 said:**
> Try booting the "Ubuntu, with Linux 4.13.0-31-generic" kernel.

And since you have it you can also try "Ubuntu, with Linux 4.4.0-112-generic".

Im crashing on both..

---

### Post by cruzer001 on 2018-01-26
Lets see if this has anything to do with power management (ACPI).  It can be turned off for testing for one session.  This link is a bit dated but shows how to remove acpi (acpi=off) for one session.

[https://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting](https://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting)

And we will modify that entry to also turn off apic.  So it will look like this:

acpi=off noapic

That is what you need to add.

---

### Post by moralesj10 on 2018-02-03
I have done what you said, twice. Both times, after entering my encryption password, it will stay on a black screen and after a minute or two, turns off the screen and does nothing else. I got a message this time when booting up, that says something about the CPU temperature and throttling. I had a similar message after I replaced the screen on this laptop, unclogged the fan, and it had been working perfectly after that. I haven't received that message until now but when I check using sensors in the terminal, it all looks fine, and it does not feel anywhere near as hot as before I noticed the fan wasnt working.

Thanks for the help!

---

### Post by cruzer001 on 2018-02-04
Hello
> 
when I check using sensors in the terminal, it all looks fine, and it does not feel anywhere near as hot as before I noticed the fan wasnt working

Did you also replace the thermal paste between the cpu and heat sink?

Even though you don't seem to run hot you may want to try bumping up your fan speeds.  there are several apps for this, here's a start.

[https://itsfoss.com/reduce-overheating-laptops-linux/](https://itsfoss.com/reduce-overheating-laptops-linux/)

That link gives a PPA for TLP, but its already in our repositories.  I did not see any mention of the app "fancontrol" that works with lm-sensors, also installable through our repositories.

One other suggestion is to create a new user account and run on it for a while.  See if the problem persist.

And last
There are the system logs that may show whats up.  The kernel log and system log (in /var/log) would be the ones to look at.

Hope this yields something, I'm out of ideas :(

---

