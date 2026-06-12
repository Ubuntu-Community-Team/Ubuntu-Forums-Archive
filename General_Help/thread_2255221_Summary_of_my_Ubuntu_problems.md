---
title: "Summary of my Ubuntu problems"
date: 2014-12-03
forum: General Help
---

### Post by Tony_Fendall on 2014-12-03
Tried to install Ubuntu on my MS Vista HP G5000 laptop.
Chose Ubuntu only option, not dual boot (probably my biggest mistake). 
Did not have a Vista disk, big mistake.
Laptop would boot into Ubuntu with no wireless and not running on battery and no way to shutdown unless power cord disconnected.
Wired Internet worked.
Could not boot from USB or CD drive.
Left over summer as I prefer to be outdoors.
Two days ago I started hacking again.
Inserted a Windows 7 recovery disk and chose recovery option which reported failed.  However after this laptop worked on battery. 
I found a good YouTube video for wireless install problems and this worked.
I only have one problem now as have others. On shutdown battery 100% drains to 0% and has to be started on mains power next morning.
So now very close to a sucessful Ubuntu install; I like Ubuntu BTW I will give new life to a struggling Vista laptop.

---

### Post by Yougo on 2014-12-03
Battery
Battery problems are a bit troublesome to pinpoint. as you say it's an old laptop. several things can be going on:
- the battery is old and can't carry a load like it used to. it says it's full but as soon as you pull the cable, it collapses to 0% and the laptop drops off. batteries can degrade fast. the battery of my old laptop was fine for 4 years, and then just died. Windows Vista never told you about this, and Ubuntu does, so now you really notice.
- your particular ubuntu install has a major power leak somewhere draining the battery. this isn't normal, and something may have gone wrong on your computer. do you notice anything like the harddrive or the fan spinning ridiculously? or is your laptop running unusually hot somewhere? is the CPU light going nuts like it's very busy?
-Your battery is fine, there is no power leak, but Ubuntu is somehow reading your battery wrong, giving you weird results and warnings.

i suspect the first option is the most likely, to be sure you'd have to ask for more help as i don't know much about linux power consumption problems.

Wireless
it really depends on what kind of wireless card brand and type you have, and what drivers you need for that. by far most cards are supported out of the box, but it seems your's isn't. testing your system by running it from the live cd before you install may catch those problems in advance.

can you press Ctrl+Alt+T? a command line terminal should show up.
(or you can click on the ubuntu logo in the top left and type 'terminal' in the menu. the program should show up and you can click on it to start it)

when you have the terminal open, type the following command and press Enter
```
 lshw -C network 
```

select the resulting text, right-click and choose copy, and then paste it in a post here.

---

### Post by Tony_Fendall on 2014-12-03
It's a fairly new upgraded replacement battery.
Since posting, it refuses to run on battery again and will not charge from mains input.
Although selected, it will no longer show time in menu bar and % in menu bar.
Any ideas, battery was fine yesterday at 100%.tony@tony-HP-G5000-GF769EA-ABU:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:80400000-80403fff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:2e:e6:10
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:67:ea:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-24-generic firmware=666.2 ip=192.168.1.131 link=yes multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
tony@tony-HP-G5000-GF769EA-ABU:~$

---

### Post by Tony_Fendall on 2014-12-03
I think I know what's happened; it's trashed my new battery; voltage too low to recover and setting was suspend on low voltage.
Should have set it to shut down on low voltage.

---

### Post by Yougo on 2014-12-04
I've heard of battery capacity declining when drained too far (a risk regardless of which os you use), but i've never heard of destroying a battery overnight this way:? this should not happen. can you still go back to the store with it? -tip: don't complicate things by mentioning Linux, keep it simple: my brand new battery is suddenly dead and i'm not happy ;-) -

i see you have a broadcom BCM4311 wireless card. these can be tricky to get going. as far as i can see, a driver has been installed.

could you run the following command and post back the results?
```

iwconfig

```

this should tell you whether the card is working but can't get a connection, or isn't working at all

please also read and follow instructions of answer number 82 on the following askubuntu.com page:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

it's extensive, but thorough.

---

### Post by Tony_Fendall on 2014-12-04
Everthing appears to be working and new battery is on order, so running on mains only at the moment.
Will report back when new battery arrives. It would be good if Ubuntu never allowed a setting other than 'shut down on low voltage' not 'hibernate' , which I think drains battery.
tony@tony-HP-G5000-GF769EA-ABU:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"BTHub5-XNF8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:62:2C:77:60:B8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:69   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

tony@tony-HP-G5000-GF769EA-ABU:~$

---

### Post by Tony_Fendall on 2014-12-05
Is there a problem with Ubuntu and laptop battery charging?  I found 6 pages of issues before I got fed up looking on Google.

---

### Post by ian-weisser on 2014-12-05
If such a battery-charging problem is reproducible on similar hardware, then it would be a bug.
If the bug is in hardware, then you have a manufacturer warranty issue.
If the bug is in Ubuntu, then is should be filed as a bug report.
If it's not reproducible, then there's not much Ubuntu can do about it. We're not psychic.

My own laptop batteries, of various models, have charged flawlessly with various Linux distros for nine years.

---

### Post by Tony_Fendall on 2014-12-05
So when I get my new battery, I will get it to 100%, shut down Ubuntu during the day, leave it on charge and check hourly the battery status.
If it starts to drain severely I am sure you guys will advise me to obtain some system data and we can go from there.
I will make sure to remove the battery overnight to ensure it does not drain to an unrecoverable level.

---

### Post by Tony_Fendall on 2014-12-15
So new battery arrived for my HP G5000 laptop and fully charged.  OS worked fine on and off mains power. Switched off overnight and the battery drained by approx 3% this morning. So if left in the laptop for several days this battery would be trashed too.
I will remove the battery on switch off as long as the terminal wear will allow.  
As many others are experiencing this 'feature', would it be appropriate to consider it a 'bug'?

---

### Post by Tony_Fendall on 2014-12-27
I have now thoroughly tested my new battery with Ubuntu and I now find battery drain to be acceptable.

---

