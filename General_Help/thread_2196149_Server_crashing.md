---
title: "Server crashing"
date: 2013-12-28
forum: General Help
---

### Post by geohei on 2013-12-28
Hi.

I have some 5 years old hardware running Ubuntu server 12.04 i386. It quite stable 24/7 during months. Since yesterday, it locked up twice without me having changed anything to the system (software and hardware). When this happened, it was coping files to another server using rcp. The server has no screen or keyboard attached. I noticed the locked system since no reply came from a ssh, ping, ... After pushing the hard reset button, system started normally again.

Before I start to investigate about some hardware issues, I'd like to know if log files (if there are any) might reveal any hint on what could possibly have happened.

Any ideas?

BTW ... I never copied files using rcp, always scp. Is it possible that rcp is buggy (hard to believe - it's basic stuff)?

Thanks,

---

### Post by Bashing-om on 2013-12-28
geohei; Hi !

How large of a file(s) were you copying ? Maybe disk space ?
Terminal commands:
```

df -h
df -i

```
Would be the 1st thing I would check. Log files always make interesting reading.

[INDENT][INDENT]just my 2 bits worth
[/INDENT][/INDENT]

---

### Post by geohei on 2013-12-28
Thanks for the hint.

No. Space is no issue. df shows plenty!

The files which I copy are image files. Quite big. Up to 6 GB. But this can't be the reason since the system hang twice using rcp at a different progress stage while coping the same directory.

BTW ... I used rsync now, and after 350 GB (total to copy is 2 TB!) it showed "Killed" in the console and the copy process stopped. No crash though! I keep on testing, but I don't really have a plan ...

---

### Post by Bashing-om on 2013-12-28
geohei; Grasping,

"Quite big. Up to 6 GB." -> fat16 file system by any chance ? (file size limitation !)

[INDENT]just another thought
[/INDENT]

---

### Post by geohei on 2013-12-29
No. I copy from ext4 to ext4. So no file size limitations from filesystem apply.

BTW ... even if a file should be too big, there's no reason to crash!

Latest rsync now also crashed the system!
I'm running  out of ideas.

What about my first question - are there any log files in the system which might give a hint?

Here the top dump at the time of the crash:
```
top - 07:16:36 up 20:24,  3 users,  load average: 1.04, 0.93, 0.86
Tasks:  80 total,   2 running,  78 sleeping,   0 stopped,   0 zombie
Cpu(s): 41.0%us, 14.6%sy,  0.0%ni, 32.9%id,  2.0%wa,  0.0%hi,  9.5%si,  0.0%
Mem:   3097776k total,  2905740k used,   192036k free,    56148k buffers
Swap:  1952764k total,        0k used,  1952764k free,  2787424k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2277 root      20   0  9344 5444 2000 R 47.8  0.2 172:59.13 ssh
 2276 root      20   0  8640 1424  944 S 14.3  0.0  50:41.49 rsync
...
```

---

### Post by 3rdalbum on 2013-12-29
Full system freeze,
Happens during something that uses a lot of memory
Six gigabyte file that's being pushed around the memory

Sounds like one of your RAM sticks is starting to fail. Try taking one out, seeing if the copy works, if it still doesn't work then put the RAM stick back in and take out another one, etc, until you find the culprit.

---

### Post by geohei on 2013-12-30
Well ... copying a file, independently of its size, should not crash the system. Anyway ... assuming it's the RAM, I let memtest86+ taking care for 6 passes. The installed 3 GBs were reported fine after 24 hours. So I assume we can skip the RAM as potential source for the freezes. Yes I know, memtest86+ is no 100% guarantee, but it's close to it.

Does the top code block in posting #5 reveal anything particular?

I believe it is weird that so much memory is used when staring rsync.

The idle situation looks like this (just after reboot, nothing running):
```
top - 09:14:22 up 57 min,  1 user,  load average: 0.41, 0.14, 0.07
Tasks:  85 total,   1 running,  84 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3097776k total,   292896k used,  2804880k free,    24604k buffers
Swap:  1952764k total,        0k used,  1952764k free,   213152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0  3512 1892 1232 S  0.0  0.1   0:00.76 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd
...
```
I noticed that, after starting rsync or rcp (doesn't matter which tool), the memory fills up completely until the leaving only #200M of the installed 3GB free (just as shown in posting #5).

Why is that?

---

### Post by geohei on 2013-12-31
Regarding the questions previous posting ... nobody knows?
(fillup of memory by rsync or rcp)

Something else ...
As I said, the server has no screen or keyboard. Now I connected both and noticed, that in fact it didn't lock up.

Initially, I had 2 ssh sessions opened. One to run rcp (or rsync) and the other one for top. After a while, _they_ froze in fact. No communication was possible anymore. Also ... a new ssh didn't connect to the server. Hence my assumption that the entire server locked up.

Now that I had a screen connected (shell running top to cross check), I noticed that after the remote computer showed the lockup symptoms as previously described, I went to the server, hit the RETURN key in order to get rid of the screens screen saver, top worked! So the server didn't lockup. Also, after (and only after!) the RETURN key hit, I could also access the server again using ssh from the remote computer.

Hence ... it seems that the server went into some sleep for some reason, killing the used sshs and rsync/rcp processes.

However this only happens when load is put on the computer like I did = copying files from this server to another server using rsync or rcp. When the server is idle, the server doesn't kill both sshs or top!

Any ideas?

---

### Post by tgalati4 on 2013-12-31
I would suspect bad power supply.  Any error messages in /var/log/syslog?

The memory usage is a result of normal linux caching.  Any process gets put into RAM in case you want to repeat the action.  There are sysctl settings that you can change to reduce the RAM footprint.

Use *htop* to get a better picture of what is happening.  The fact that the keyboard and mouse keeps your system going tells me that extra energy is stored in them (as a buffer) when your power supply sags.

I had a server that was acting strange--a power connector had come loose on the back of a hard disk.  It would freeze--waiting for the disk to spin up, but not die.  IOWaits increated as a result.  This does not appear to be your problem, but any loose cable could interrupt normal operation.

---

### Post by geohei on 2014-01-01
Thanks for the reply.

I downloaded htop. Looks better than top!

I sent you the syslog/syslog.1 via PM. I don't see anything suspicious.

I don't really follow your power supply assumption. Do you mean that there is is a power supply problem in terms of components sucking too much power (e.g. HDD simultaneous spinup) or do you mean a bad connector?

I did not configure any spindown, so the HDDs turn 24/7. Also, if the spinup would be a problem, why would this happen in the middle of the copy process (sometimes after 5 minutes, sometimes 5 hours only). Any why would the ssh connections to other remote computers drop, like it happens to me?

If I would suspect a hardware defect, I'd go in the NIC direction, but I don't really see what how the data transfer could kill 2 ssh and one rsync/rcp process and could disallows future ssh logins until the a key is pushed on the keyboard.

I could test to copy data to an internal partition which has free space, thus leaving the NIC idle. I'll try that one ...

---

### Post by tgalati4 on 2014-01-01
As I stated in my pm, you have some random shutdowns--one showing a drm radeonfb panic (video framebuffer on the radeon card had a problem) and another at a random time later.  I would suspect that your power supply is sagging--dropping below 12VDC or 5VDC at random times.  That will cause problems that are not completely captured by the system logs.  Check the voltages with a voltmeter.  Swap power supplies with another one.

---

### Post by geohei on 2014-01-02
Looking at the timestamp of the shutdowns, I believe that these were the hard resets (I pushed the button) triggered by myself since I was assuming system lock w/o attached screen/keyboard.

But now ... I did what I announced in my previous article. I copied the data from one hard disk to another spare HDD locally. At the same time, I kept 2 instances of ssh open to that server from my desktop. No ssh disconnects anymore for +24 hours! The system was working close to 100% CPU load all the time, during an entire day. Both ssh sessions remained connected. This test stresses the PSU even more than the LAN transfer, hence I'm not really sure about the idea with the faulty power supply (but I keep it in my pocket!).

So ... it's only the data transfer via NIC which disconnects the existing ssh sessions, disallows future ssh sessions and kills the rcp/rsync process.

Next thing. Very basic. I replaced the LAN cable. The problem seems to be NIC related.

If the cable is defect, is there any place I could possibly check for retransmitted local packages (ifconfig?)? This would confirm the NIC issue (not necessarily the cable idea).

---

### Post by geohei on 2014-01-02
It wasn't the cable.

After a hit on keyboard, ssh was available again (as before). The code block below was taken right after NIC was reactivated (hit on keyboard).
```
...
Jan  1 17:17:01 testbox CRON[9502]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 18:17:01 testbox CRON[9516]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 19:17:01 testbox CRON[9535]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 20:17:01 testbox CRON[9558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 21:17:01 testbox CRON[9585]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 22:17:01 testbox CRON[9607]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 22:22:39 testbox kernel: [223535.463699] via-rhine 0000:00:12.0: eth0: link down
Jan  1 22:23:34 testbox kernel: [223590.622306] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan  1 23:17:01 testbox CRON[9652]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 00:17:01 testbox CRON[9677]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 01:17:02 testbox CRON[9702]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 02:17:01 testbox CRON[9728]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 03:17:01 testbox CRON[9757]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

So ... it wasn't the NIC.

Next idea ... is there any power reducing mechanism which might turn off the NIC?

Thanks,

---

### Post by tgalati4 on 2014-01-02
Since this machine is older, have you thoroughly cleaned out the machine with compressed air?  All it takes is some dust on the motherboard controller chips to cause these kinds of problems.  If it was truly a kernel or software problem, you would have consistent and extensive error messages.  When you have hardware errors, you don't get extensive logs or any logs at all, just random behavior.

NIC cards/chipsets can fail from voltage spikes.  One bad capacitor on the motherboard can cause problems.  Are there any bulging or leaky capacitors on the motherboard?

The good news is that your CPU and supporting motherboard circuitry seem to be working OK, but the issues become evident with networking and file transfers.  So try reseating RAM, changing port connections, cables, and cleaning the router--since that could be causing problems as well.

---

### Post by geohei on 2014-01-04
I'll visually check the hardware!

Meanwhile ... ifconfig after restart:
```
eth0      ...
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16034 (16.0 KB)  TX bytes:12107 (12.1 KB)
          Interrupt:23 Base address:0x4000
```
ifconfig after 1 minutes of rcp transfer. Dropped packets. Guess this is not normal. The remote server where the copy is being transferred to, it connected via LAN (2 meters away, switch in between).
```
eth0      ...
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137079 errors:0 dropped:4 overruns:0 frame:0
          TX packets:404489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9316259 (9.3 MB)  TX bytes:608934625 (608.9 MB)
          Interrupt:23 Base address:0x4000
```
... later ...

Google search revealed (ubuntu ifconfig rx packets dropped):
[http://sysadmin-notepad.blogspot.com/2013/06/dropped-rx-packets-in-ifconfig.html](http://sysadmin-notepad.blogspot.com/2013/06/dropped-rx-packets-in-ifconfig.html)

They talk about the ring buffer, which I don't seem to have.
```
root@testbox:~# ethtool -g eth0
Ring parameters for eth0:
Cannot get device ring settings: Operation not supported
```
Many issues regarding rx packet drop seem to ring buffer related. However I don't have such ring buffer !?!?
Could it be some other kind of NIC (buffer) issue, other than hardware related?

... later ...

Or could it be a routing problem?

---

### Post by geohei on 2014-01-05
Someting more ...
```
root@testbox:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:09.0 RAID bus controller: Intel Corporation RAID Controller
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV100 [Radeon 7000 / Radeon VE]
root@testbox:~# dmesg | grep hine
[    1.403241] via_rhine: v1.10-LK1.5.1 2010-10-09 Written by Donald Becker
[    1.403261] via_rhine: Broken BIOS detected, avoid_D3 enabled
[    2.095236] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    2.100771] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xe0115000, 00:xx:xx:xx:xx:xx, IRQ 23
[    2.101490] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1
[    8.674435] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```
What about "Broken BIOS detected, avoid_D3 enabled"?
This VIA Rhine II VT6102 seems to create tons of different issues (Google). Much read, but not anything resolving my problem.

---

### Post by tgalati4 on 2014-01-05
You need to use *sudo* with *ethtool* to set anything.  VIA chipsets may not have the reliability of Intel chipsets--or any other chipset.  4 dropped packets is not a lot for 600 MB of transfers.  It could simply be interference since your switch is close (2m).  Try a longer cable (3m or 5m).

Don't know about the D3 state.  Perhaps it is related to Wake-on-Lan:

tgalati4@Mint14-Extensa ~ $ modinfo via-rhine
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/ethernet/via/via-rhine.ko
license:        GPL
description:    VIA Rhine PCI Fast Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     C7A75132473BDEA87B06C85
alias:          pci:v00001106d00003053sv*sd*bc*sc*i*
alias:          pci:v00001106d00003106sv*sd*bc*sc*i*
alias:          pci:v00001106d00003065sv*sd*bc*sc*i*
alias:          pci:v00001106d00003043sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           **debug:VIA Rhine debug message flags (int)**
parm:           rx_copybreak:VIA Rhine copy breakpoint for copy-only-tiny-frames (int)
**parm:           avoid_D3:Avoid power state D3 (work-around for broken BIOSes) (bool)**

You can turn debug on to get more information on what is going on.

A Haiku:

My Yugo makes noise.
Built that way.  No easy fix.
My Via server . . .

---

### Post by geohei on 2014-01-06
> **tgalati4 said:**
> ...
You can turn debug on to get more information on what is going on.
...
How can I do that?

---

### Post by geohei on 2014-01-07
Next thing ... I tested Ubuntu 13.10 Desktop live version.
No errors anymore!
How come?
What's the difference between 12.04 Server and 13.10 Desktop regarding networking (via_rhine driver?)?
What can I change in 12.04 in order to get it to work?
Is it possible to "upgrade" the 12.04 via_rhine driver in order to match 13.10 version?

So ... my hardware is fine.

I guess I have to install 13.10 Server i386 (64-bit doesn't run on that one)!

```
root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
...
          RX packets:58228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6073295 (6.0 MB)  TX bytes:255361305 (255.3 MB)
...
root@ubuntu:~# modinfo via_rhine
filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/ethernet/via/via-rhine.ko
license:        GPL
description:    VIA Rhine PCI Fast Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     332ADF5086770B9F74F89A1
alias:          pci:v00001106d00003053sv*sd*bc*sc*i*
alias:          pci:v00001106d00003106sv*sd*bc*sc*i*
alias:          pci:v00001106d00003065sv*sd*bc*sc*i*
alias:          pci:v00001106d00003043sv*sd*bc*sc*i*
depends:        mii
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686
parm:           debug:VIA Rhine debug message flags (int)
parm:           rx_copybreak:VIA Rhine copy breakpoint for copy-only-tiny-frames (int)
parm:           avoid_D3:Avoid power state D3 (work-around for broken BIOSes) (bool)
```

---

### Post by geohei on 2014-01-08
Ok ... I was too fast.
Initially no dropped packets for a long time, then again network lockup with 25% dropped packets as seen on local console. No remote login possible anymore until local keyboard was touched.

Let's get back to the hardware. I opened the box. completely cleaned. Not much dust. Successive test still failed. Elcos checked. All (!) big ones (capacity unknown) show big belly, but none exploded so far or shows this typical brownish liquid getting out on top of the crossed ridges of the elcos. All smaller elcos optically seem to be ok.

BTW ... this is the motherboard:
[http://www.ecs.com.tw/website2008/Product/Product_Detail.aspx?CategoryID=1&DetailID=63&DetailName=Feature&MenuID=24&LanID=0](http://www.ecs.com.tw/website2008/Product/Product_Detail.aspx?CategoryID=1&DetailID=63&DetailName=Feature&MenuID=24&LanID=0)

---

### Post by tgalati4 on 2014-01-08
I have a few machines with ECS motherboards and they have been reliable with SiS chipsets.  

Any capacitors that are bulging are bad.  Those crosses on top of the capacitors are designed to burst to relieve pressure.  When capacitors break down, they heat up and create gas which makes them bulge.  The electrical short inside will cause the voltage to sag causing mysterious problems.  So either repair the motherboard or scrap it.

There is no linux distro that will work with [bad capacitors]("http://www.eventsentry.com/blog/Bad.jpg").

---

### Post by geohei on 2014-01-12
> **tgalati4 said:**
> ...
There is no linux distro that will work with [bad capacitors]("http://www.eventsentry.com/blog/Bad.jpg").
I'll change them ... and post the outcome.

---

### Post by geohei on 2014-01-30
> **geohei said:**
> I'll change them ... and post the outcome.
All 9 capacitor changed.
The transfer errors remain!

---

### Post by tgalati4 on 2014-01-30
Put in a new network card.  It's possible that your networking chip gets hot during long file transfers--put your finger on it during a transfer and see how hot it is.  On some boards the networking chip is also part of the southbridge chip, which handles other motherboard functions such as memory.  So put your finger on all of the exposed chips and if there are any that are too hot to keep your finger on, then take note of the chip number and do some research on the chip's functions.

If a new network card fixes the problem, then at least you have a work-around until something else fails.

---

### Post by geohei on 2014-01-31
Thanks for the hint, but I'll change the motherboard now. Not gonna waste more time on that one.

Also ... the dropped packets show up right upon startup, so when everything is still nicely cool. Hence, heat can't be the reason.

The only problem is that I'd like to keep my existing hardware. Therefore I need a motherboard which supports:
- >= 3 DIMMs sockets (2 sockets are enough, but +2 are preferential).
- AMD ATHLON XP 3000+
- PCI slot
- IDE
- Onboard graphics (preferential)

Since these specifications are pretty old, it's hard to find such a motherboard.
The only thing I found was: [ASRock]("http://geizhals.de/asrock-k7s41gx2-pc3200-ddr-a767243.html")

---

### Post by geohei on 2014-02-04
Ok ... something new.

Just by chance, I found out that a second server (running ubuntu 12.04 server), which is hooked up to the same switch as the initially faulty server (also running ubuntu 12.04 server, hardware = 4 years old), is also producing dropped packets. Strange coincidence! I didn't check its motherboard yet.

Also ... another device (RasperryPi) is also connected to this switch. No dropped packets on that one! There are also other Linux computers hooked to the same LAN. No dropped packets.

How come that 2 ubuntu servers show, within a relatively short time frame, the same error?

Weird!

Could there be anything within the network which might create these dropped packets on ubuntu servers and not on other operating systems.

---

### Post by tgalati4 on 2014-02-04
It could be traffic collisions within the router.  Try rearranging ports, check for any policies on those ports, then reboot the router.

---

### Post by geohei on 2014-02-08
The new motherboard does exactly the same. Dropped rx packets.

I investigated further ...
[http://www.google.lu/#q=ubuntu+dropped+packets+why](http://www.google.lu/#q=ubuntu+dropped+packets+why)

I'm not alone ...
[http://ubuntuforums.org/showthread.php?t=1763297](http://ubuntuforums.org/showthread.php?t=1763297)
But it seems to be as per design ...
[http://www.novell.com/support/kb/doc.php?id=7007165](http://www.novell.com/support/kb/doc.php?id=7007165)

In other works ... it's normal!

So ... probably it would not have been necessary to change the motherboard ... :(

---

### Post by tgalati4 on 2014-02-08
Search on how to shut off IPV6.  This could be the issue:  *IPv6 frames when the server is not configured for IPv6*

---

