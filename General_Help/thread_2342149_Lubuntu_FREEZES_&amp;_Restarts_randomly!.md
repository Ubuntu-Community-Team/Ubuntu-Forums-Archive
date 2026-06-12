---
title: "Lubuntu FREEZES &amp; Restarts randomly!"
date: 2016-11-04
forum: General Help
---

### Post by mitizaro on 2016-11-04
Dear Forum.

I have this old Toshiba Core 2 Duo Laptop. I gotta make use of it for now.

Decided to install 16.04 LUBUNTU 32bit. Great decision!! It is amazing OS, but my laptop freezes, restarts or just crashes its screen at totally RANDOM times!

Sometimes it will work for hours, sometimes i will get it <snip> 10 times for 10 minutes.

It is NOT dependent on activity. I can sit it idle, or run the heaviest load -- sometimes it will crash, sometimes totally not!

I've also noticed that while i tried to install Windows 10 using USB OR CD -- the laptop did the same issues (and i cant really get to the end of the installer at all).

Given said that it's probably not Lubuntu's fault... but can't we figure some remedy or at least the cause?

I will search for command to display my laptop specs in the mean time. Just in a hurry to save this message before i crash it again! :D

Thank you,
Dimitar

---

### Post by cariboo on 2016-11-04
To get the specs of your laptop, install inxi and run:

```
inxi -b
```

the output should look something like this:

```
inxi -b
System:    Host: alexis Kernel: 4.8.0-27-generic x86_64 (64 bit)
           Desktop: Unity 7.5.0
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   System: TOSHIBA (portable) product: Satellite C50-B v: PSCMLC-02Y00T
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           UEFI: TOSHIBA v: 1.70 date: 12/11/2014
Battery    BAT1: charge: 12.2 Wh 60.7% condition: 20.1/22.0 Wh (91%)
CPU:       Quad core Intel Pentium N3530 (-MCP-) speed/max: 499/2582 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 12.0.3
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
Drives:    HDD Total Size: 750.2GB (4.6% used)
Info:      Processes: 260 Uptime: 2:42 Memory: 1455.9/3838.1MB
           Client: Shell (bash) inxi: 2.3.1 
```

As far as your shutdown problems are concerned, could it be heat related. I personally use psensors to monitor my laptops performance:

```
sudo apt install psensors
```

---

### Post by mitizaro on 2016-11-05
System:    Host: MitYoCave Kernel: 4.4.0-45-generic x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA (portable) product: Satellite L300 v: PSLB0E-01G019B3
           Mobo: Intel model: N/A Bios: INSYDE v: 1.30 date: 03/19/2008
CPU:       Dual core Intel Pentium Dual T2370 (-MCP-) speed/max: 1333/1733 MHz
Graphics:  Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.00hz
           GLX Renderer: Mesa DRI Intel 965GM GLX Version: 2.1 Mesa 11.2.0
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           Card-2: Realtek RTL8187B Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 250.1GB (4.1% used)
Info:      Processes: 183 Uptime: 6 min Memory: 717.4/1990.7MB
           Client: Shell (bash) inxi: 2.2.35 


THANK YOU kind sir!

Now i dont think its heat related. As a matter of fact, when the room is colder, or when i first turn on the laptop from night's being shut down -- it is the worst!

Also as i said it happens very often if i DON'T use the laptop at all.

I also noticed that the disk utility in ubuntu said i have 170 bad sectors... probably the HDD is the cause. But CAN IT cause such kind of crashes, or is something wrong with the processor?

WHen i try to mount certain partitions (the NTFS ones primarily -- reminents of the Windows attempts to install on this laptop) -- the laptop ALWAYS immediatelly crashes so i assume HDD fault.

My brother has sent me his spare HDD and i will install it (removing the old). However i wonder IF THE HDD can cause such freezes, restarts and etc.

---

### Post by RobGoss on 2016-11-05
> I also noticed that the disk utility in ubuntu said i have 170 bad sectors... probably the HDD is the cause. But CAN IT cause such kind of crashes, or is something wrong with the processor?


Having a failing hard drive can and will, cause all sorts of problems including not booting one day don't be surprise when booting you see errors messages this is normal with a failing drive. I would recommend backing up any important date and documents just incase something goes wrong

Having bad sectors in a clear indication sometime is wrong with that hard drive if you like you can read about this problem here: [http://askubuntu.com/questions/241944/how-to-fix-the-hard-drive-bad-sector](http://askubuntu.com/questions/241944/how-to-fix-the-hard-drive-bad-sector)

---

### Post by Autodave on 2016-11-05
A failing HD can cause those problems, but it is more likely a RAM failing or mother board failing. Since you have the other HD, you may as well try it first.

---

### Post by mitizaro on 2016-11-05
I HOPE its the HDD.

The laptop is old. I tried using the bios settings and disabled the second core of the processor, and made the temps to hold low (i.e. low activity)

NO RESULT -- still crashed the same. So it leads me to the idea that it is NOT the processor.

I hope its not motherboard. But it could be RAM. During my linux PUPPY sessions it happens as well. And puppy doesn't really use the HDD much.

However it does NOT happen when i increase the load! It happens actually mostly when i do NOT use the laptop!!

I HOPE it is hdd, since i won't be able to replace anything else.

I HOPEFULLY plan to get new laptop in 2-3 months... so i gotta patch this one for just a few more weeks!!


Let me further explain the crashes -- sometimes i get this screen, where the colors and evrything is chaos -- and its frozen as well. Sometimes its just the normal screen but frozen. Somtimes it restarts itself.|


P.S. - Forgot to mention The battery (or something with the charging port) is damaged and essentially the laptop woks only if its plugged in. If i plug it out - it stops. But i have secured it pretty tight and i NEVER move it, so i highly doubt this has anything to do with it.

I will also run memtest tomorrow for a few hours.

---

### Post by mitizaro on 2016-11-06
Today noticed using PSensor that while it was restarting - Core 0 temp was still 38 degrees, other temps were about 40-45 (Celisus).

This means that the problem is absolutely no OVER-heating, but could it be under-heating???

OTOH if its the HDD, then temps are irrelevent and untill it "spins a little bit enough" it will be crashy. HOPE it fixes tomorrow with the new hdd.

Also if i use the laptop regularity (open tabs, browse, etc.) and not leave it to be idle -- it is much better. This brings me hope its not the RAM.

---

