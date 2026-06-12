---
title: "[SOLVED] Dear god, someone help me!"
date: 2008-06-28
forum: General Help
---

### Post by Famicommander on 2008-06-28
This issue has me smashing my head against my keyboard. simple terms, I'm stuck at 800x600 resolution and nothing suggested in Absolute Beginner talk has helped.

All of the details, as well as what has been tried and failed, can be found here:
[http://ubuntuforums.org/showthread.php?t=843061](http://ubuntuforums.org/showthread.php?t=843061)
 
I know my way around an Ubuntu PC fairly well and I can usually solve my own problems, but in this case treat me as if I know nothing. I need simple, step by step instructions before my head explodes.

---

### Post by Max Spain on 2008-06-28
Do you know what kind of video card it has.  If not, try lspci in the terminal.

---

### Post by Famicommander on 2008-06-28
> **Max Spain said:**
> Do you know what kind of video card it has.  If not, try lspci in the terminal.

Here's what it gives me:
```
jason@ubuntu:~$ lspci
00:00.0 Host bridge: ALi Corporation M1621 (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)

```

---

### Post by wdaniels on 2008-06-28
I did a little research for you and found [this thread on the Dream Linux forums]("http://dreamlinuxforums.org/index.php/topic,2411.30.html"). It's not 100% clear what changes are needed, but a working xorg.conf is posted there.

First make sure the trident driver is installed:

```
sudo apt-get install xserver-xorg-video-trident
```

Then edit the Device and Monitor sections in xorg.conf as follows:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver       	"trident"
	Option	"Monitor-VGA"	"My Monitor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-70
	VertRefresh	50-120
	Option    "DPMS"
	Modeline	"1024x768"  64.11  1024 1080 1184 1344  768 769 772 795 -HSync +Vsync
	Option	"PreferredMode"	"1024x768" 
EndSection

```

Reboot and see if it makes any difference.

---

### Post by Famicommander on 2008-06-28
No dice.

Still in the same boat.

---

### Post by Famicommander on 2008-06-28
You aren't going to believe this, but it's working. I punched the keyboard, the screen flashed, and now it's working.

Thanks for all of your help.

---

### Post by jimv on 2008-06-28
> **Famicommander said:**
> I punched the keyboard, the screen flashed, and now it's working.

I don't think that's in the troubleshooting guide for video problems.

---

### Post by Famicommander on 2008-06-28
> **jimv said:**
> I don't think that's in the troubleshooting guide for video problems.
Well, maybe it should be.

---

