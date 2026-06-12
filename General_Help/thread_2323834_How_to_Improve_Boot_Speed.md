---
title: "How to Improve Boot Speed"
date: 2016-05-08
forum: General Help
---

### Post by convert_mrta on 2016-05-08
Hello,  I've got a laptop running U14.04 LTS with 4 GB of ram, plenty of empty disk  which takes 1:43 to boot to my login prompt.   I've got bootchart installed, and generated the attached chart.  Can anyone suggest what I can do to greatly improve my boot speed?

[ATTACH=CONFIG]268933[/ATTACH]

I'd also like to know what the vertical dotted line means which appears on any bootchart diagram.

Thanks very much!

---

### Post by RobGoss on 2016-05-08
Hello and welcome to the forum, The chart is not readable for me so I couldn't make anything of it but from my experience I normally try to improve my startup time by trimming down those programs that will automatically startup when your machine is turned on

When you boot up your machine try to find the** Startup Application, **there you can choose which programs you want to boot up and the ones you don't, just UN-check the one you don't then close the menu and reboot your machine. It should help with startup time. 

I really find that Compiz  is one of the biggest problems which effects most desktops with Ubuntu I'm not sure if you are running any of these application at start but if so you might want to disable them at startup just wanted to mention that.

---

### Post by oldfred on 2016-05-08
I prefer to look at /var/log/dmesg with 14.04. May not be in 16.04.

And then you only need to review those with long time stamp differences. No need to post entire file as it is long.

Example from my 14.04, but last entry was at 5.4 as SSD boots very fast.
```
[    2.433721] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    4.914618] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro

```

What I am not sure of is if time stamp is start or end. Or if nVidia is slow or if mounting ext4 is slow.

---

### Post by convert_mrta on 2016-05-09
Hi Rob.   I have already reviewed everything that's autostarting, both apps and services, so they aren't the problem.

OldFred - "you only need to review those with long time stamp differences"   Looking at my /var/log/dmesg, I don't even see time stamps.

I see what seem to be line numbers.   Last six lines in my log, for example.   Where do I see the difference?

[   40.129232] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   40.129234] i915 0000:00:02.0: registered panic notifier
[   40.135634] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   40.149822] acpi device:0a: registered as cooling_device2
[   40.180132] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input18
[   40.189479] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0


Thanks

---

### Post by oldfred on 2016-05-09
All those entries are at 40 sec into boot process. Those are the timestamps.
You must have some with large gaps to even jump to 40 sec on those entries.

---

### Post by RobGoss on 2016-05-09
> **convert_mrta said:**
> Hello,  I've got a laptop running U14.04 LTS with 4 GB of ram, plenty of empty disk  which takes 1:43 to boot to my login prompt.   I've got bootchart installed, and generated the attached chart.  Can anyone suggest what I can do to greatly improve my boot speed?

[ATTACH=CONFIG]268933[/ATTACH]

I'd also like to know what the vertical dotted line means which appears on any bootchart diagram.

Thanks very much!


Question? what operating system did you have on this laptop before you installed 14.04 LTS I'm wondering how it performed as well.

If you're not content with **14.04** **LTS** you might consider the latest **16.04 LTS** to see if it run better. I have it on this desktop that I'm using and it runs like a champ, just a thought

I also came across this post at AskUbuntu forums [http://askubuntu.com/questions/10290/how-do-i-improve-boot-speed](http://askubuntu.com/questions/10290/how-do-i-improve-boot-speed) it give you ways to impove your startup

---

### Post by convert_mrta on 2016-05-09
OK, big jumps here:

[   10.689033] EXT4-fs (sda2): recovery complete
[   10.699880] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   28.837670] efivars: duplicate variable: PCI_COMMON-aca9f304-21e2-4852-9875-7ff4881d67a5
[   29.969396] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

Other than that, there is steady activity from 0.00000 to 40.189479.  But my PC does NOT boot in 40 seconds!  I WISH!  So dmesg isn't capturing the whole boot sequence.    Bootcharts counting ~1:43 each boot.   I'm going to config for autologin, reboot and put a stop watch on it.  I'll let you know.

Thanks all for the leads.

---

### Post by DuckHook on 2016-05-09
It is unnecessary to upgrade. That is too drastic surgery for what is likely a minor ailment and is unwise at this time.

In addition to oldfred's advice, you can also do the following:```
sudo nano /etc/default/grub
```Erase the options```
quiet splash
```Then:```
sudo update-grub
```...this gets rid of the splash screen when you are booting up and shows you all of the processes as they load. You will then see in real time what processes are holding up your boot time. This doesn't give you any more info than oldfred's dmesg inquiry, but sometimes it is more intuitive to actually see the problem in real time. By cross-referencing your now-visible boot experience with dmesg, you should be able to pinpoint the culprit boot process(es).

Be sure to reactivate *quiet splash* and run *sudo update-grub* if you want to get your splash screen back afterwards.

---

### Post by mc4man on 2016-05-09
> **oldfred said:**
> 

What I am not sure of is if time stamp is start or end. Or if nVidia is slow or if mounting ext4 is slow.
There's some varying thoughts here & likely more to be found. (cmks answer make most sense to me
[http://askubuntu.com/questions/749419/making-sense-of-time-in-dmesg/749455](http://askubuntu.com/questions/749419/making-sense-of-time-in-dmesg/749455)

---

### Post by convert_mrta on 2016-05-10
Duckhook,

I don't have any quiet splash statement in my grub.   And -- I see a bunch of text text flying by as my machine boots (processes loading?)   I can't really tell as they fly by so fast.  Is there a log that records what appears on screen?

So, I put a stop watch on my boot.  Upon cold start it took 55 seconds to get to my MDM login prompt.   Typed login and PW and at 1:32 I have a fully loaded desktop.  

Then I reset to auto-login.  Cold booted.   Got to Desktop again at 1:32.

So it seems that the boot time reported by bootchart is from power on all the way to desktop.   37 seconds for a desktop to appear seems slow to me.  I don't have any widgits or panel apps starting....just a sysmon CPU graph, weather, clock, network applet, battery, volume control.

---

### Post by oldfred on 2016-05-10
dmesg is the log of the screen you see when booting.

I have had SSD for about 5 years, but before that my BIOS systems booted in about 40 sec when Windows XP took 3 to 5 minutes(needed chkdsk it turned out).

I do believe Unity has more overhead, is that what you use? But still should not be that long.

Have not seen a duplicate efivars error, but that may be worth investigating. Something unique about your install? Is it booting in BIOS or UEFI mode?
You may need boot parameter, what brand/model system?

---

### Post by convert_mrta on 2016-05-10
Booting UEFI.   My desktop is MATE.

The only possibly unusual thing about my install is that I'm running MATE desktop on Ubu.  In he past, I have run Mint MATE and would have on this (then) new laptop.  But my live USB would not boot in UEFI.  So I installed Ubuntu, then installed MATE.

I have an ASUS D550MA

---

### Post by oldfred on 2016-05-10
Some of these may be close enough to yours. Are you using boot parameters?
They seem to need this boot parameter. pci=nomsi

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)

---

### Post by convert_mrta on 2016-05-10
Oh geeeeze.  Down the UEFI rabbit hole . . :frown::roll:    That was a pain when I first had to install Ubu instead of Mint.   I shiver at the thought of going through that again.   Fortunately both Ubuntu and Mint have found ways to work with UEFI since then.

---

