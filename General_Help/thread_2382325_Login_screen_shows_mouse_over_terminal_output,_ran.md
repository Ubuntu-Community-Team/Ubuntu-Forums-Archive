---
title: "Login screen shows mouse over terminal output, random pixels at top of screen"
date: 2018-01-11
forum: General Help
---

### Post by Phasmus on 2018-01-11
I reinstalled regular Ubuntu 16.04 (the latest image) on my old IBM/Lenovo X60 ThinkPad laptop with Intel graphics and everything seemed to work fine. Then I did a full update and rebooted and the GUI was effectively dead. After some weird activity during boot (a screen of vertical gray gradient) I get a 'login screen' with a mouse pointer over the console output from bootup. It doesn't look like the mouse can interact with anything. If I switch to a tty and back the mouse will be over the output from the previous tty.  At the very top of the screen, tty or login, there is a narrow stripe of 'Ubuntu purple'. When I move the mouse this stripe gradually fills with seemingly random pixels. The bottom of the tty is cut off so I can't see what I'm typing when the cursor is at the bottom, presumably shoved below the visible screen, by this stripe.

I'm really regretting my reinstall since this laptop has been solid for ages and I'm not sure what might have changed. It is possible this was caused by a recent software update and my re-installation is coincidental to the fault. There are no errors in my Xorg.0.log and I'm not sure where else to look or what action to take. Any ideas? Thanks!

System Info:
```
System:    Host: sargon Kernel: 4.13.0-26-generic x86_64 (64 bit gcc: 5.4.0) Console: tty 1
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 1709CTO v: ThinkPad X60
           Mobo: LENOVO model: 1709CTO Bios: LENOVO v: 7BETD7WW (2.18 ) date: 11/20/2008
CPU:       Dual core Intel Core2 T7200 (-MCP-) cache: 4096 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 7980 
           clock speeds: max: 2000 MHz 1: 1333 MHz 2: 1000 MHz
Graphics:  Card: Intel Mobile 945GM/GMS 943/940GML Express Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.org 1.19.5 drivers: intel (unloaded: fbdev,vesa)
           tty size: 128x48 Advanced Data: N/A out of X
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-26-generic
Network:   Card-1: Intel 82573L Gigabit Ethernet Controller driver: e1000e v: 3.2.6-k port: 2000 bus-ID: 02:00.0
           IF: ens2 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k bus-ID: 03:00.0
           IF: wls3 state: down mac: <filter>
Drives:    HDD Total Size: 120.0GB (6.7% used) ID-1: /dev/sda model: FUJITSU_MHV2120B size: 120.0GB temp: 40C
Partition: ID-1: / size: 107G used: 4.7G (5%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: 47.0C
           Fan Speeds (in rpm): cpu: 2754
Info:      Processes: 125 Uptime: 14 min Memory: 186.8/2992.9MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

---

### Post by cruzer001 on 2018-01-11
There has been mention of kernel failures in the forums lately.  I don't know for sure this is your problem, but it wouldn't hurt to switch back to the previous kernel at boot and see if thats it.

---

### Post by Phasmus on 2018-01-12
It looks like the new kernel is the problem. Reverting did the trick. 
Update: The bug was reported here and the grub workaround worked for me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639)

---

### Post by cruzer001 on 2018-01-12
Your running HWE kernel.  I find running the original 4.4.0.xxx kernel keeps me out of trouble most of the time and its supported for the life cycle of the LTS.

):P

---

### Post by DuckHook on 2018-01-12
> **Phasmus said:**
> It looks like the new kernel is the problem. Reverting did the trick. I haven't seen anyone else mention this specific issue though so I guess I ought to figure out how/where to report this...
Although the devs are getting snowed under with problems not of their own making, you can report this issue on [launchpad]("https://launchpad.net/"). You may have to create an account.
> **cruzer001 said:**
> Your running HWE kernel.  I find running the original 4.4.0.xxx kernel keeps me out of trouble most of the time and its supported for the life cycle of the LTS.
It is perfectly acceptable to run the original kernel series. But I've upgraded many of my machines (over two dozen bare metal and VMs) to HWE stack and they run fine. OTOH, wife was still on original kernel series because I thought as you did. Then: [https://ubuntuforums.org/showthread.php?t=2382157](https://ubuntuforums.org/showthread.php?t=2382157)

I guess this just shows that, old or new, kernels are susceptible to regressions and bad patches. OSes are just darn complicated & cussed things. :(

---

