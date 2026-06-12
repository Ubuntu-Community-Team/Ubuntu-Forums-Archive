---
title: "Not Waking Up From Suspend (Ubuntu 12.04)"
date: 2013-10-22
forum: General Help
---

### Post by RCAProduction on 2013-10-22
I have read up on other threads, but this doesn't seem to be quite what other people have had. This computer isn't a laptop, which may make a difference?

Here's the problem: If I click suspend, it turns the screen off (as it should), but none of the keys or mouse will wake it back up. A few seconds on the power button is also useless. When I press any button on the monitor, it says that it is in sleep mode, and to wake it press any key or move mouse, before returning to off. It isn't just a black screen, which has me stumped.

Any ideas?

---

### Post by Toz on 2013-10-22
Hello and welcome to the forums.

To show which devices are configured for wakeup, type the following command in a terminal window and post back the results:
```
cat /proc/acpi/wakeup
```

To help identify the devices, the two following commands will help:
```
lspci
```
...and:
```
lspci -t
```

If the keyboard/mouse channels are available, you can enable them to wake up the system by running a command like:
```
echo <DEVICE> | sudo tee /proc/acpi/wakeup
```
...where <DEVICE> is the device name you wish to enable.

Post back the results of those commands and lets see what you have.

---

### Post by RCAProduction on 2013-10-22
Here are the results: 


```
cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
PCI0      S5    *disabled  no-bus:pci0000:00
HUB0      S5    *disabled  pci:0000:00:1e.0
UAR1      S5    *disabled  pnp:00:07
USB0      S1    *enabled   pci:0000:00:1d.0
USB1      S1    *enabled   pci:0000:00:1d.1
USB2      S1    *enabled   pci:0000:00:1d.2
USB3      S1    *enabled   pci:0000:00:1d.3
USBE      S1    *enabled   pci:0000:00:1d.7
MODM      S5    *disabled  
```


And:


```
lspci -t
-[0000:00]-+-00.0
           +-01.0-[01]--+-00.0
           |            \-00.1
           +-06.0
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[02]--+-01.0
           |            +-02.0
           |            \-07.0
           +-1f.0
           +-1f.2
           +-1f.3
           \-1f.5
```

Followed by:
 
```
lspci
00:00.0 Host bridge: Intel Corporation82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation82865G/PE/P AGP Bridge (rev 02)
00:06.0 System peripheral: IntelCorporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: IntelCorporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: IntelCorporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: IntelCorporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: IntelCorporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: IntelCorporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: IntelCorporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller:Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev02)
01:00.0 VGA compatible controller:Advanced Micro Devices, Inc. [AMD/ATI] R300 [Radeon 9700/9700 PRO]
01:00.1 Display controller: AdvancedMicro Devices, Inc. [AMD/ATI] R300 [Radeon 9700 PRO] (Secondary)
02:01.0 FireWire (IEEE 1394): TexasInstruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: 3ComCorporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:07.0 Ethernet controller: QualcommAtheros AR5212/AR5213 Wireless Network Adapter (rev 01)
```


The last one doesn't seem to work...


bash: syntax error near unexpectedtoken `|'

NOT using USB for keyboard or mouse, if that matters.

---

### Post by Toz on 2013-10-22
Can you go into the system bios and look for an option something like "acpi" or "sleep modes". Look for something that talks about S-modes (S1, S2, S3, S4, S5). If you find it, what is it currently set at and what options are available? Let me know if there is an online manual available for your motherboard/bios.

And also, can you run the following command and post back the link that is generated:
```
pastebinit /var/log/dmesg
```
If it complains that pastebinit isn't installed, you can install it via:
```
sudo apt-get install pastebinit
```

---

### Post by RCAProduction on 2013-10-22
There is (in ACPI) PowerOn Suspend (S1) and Suspend to RAM (S3). Default is set to PowerOn Suspend.

Here is the link: [http://paste.ubuntu.com/6286722/](http://paste.ubuntu.com/6286722/)

---

### Post by Toz on 2013-10-23
> **RCAProduction said:**
> There is (in ACPI) PowerOn Suspend (S1) and Suspend to RAM (S3). Default is set to PowerOn Suspend.
Can you try changing it to S3 (Suspend to Ram). See if that makes a difference. Also, post back again, after making the change:
```
cat /proc/acpi/wakeup
```
...and
```
pastebinit /var/log/dmesg
```
...and try another suspend and see if it wakes up properly.

---

### Post by RCAProduction on 2013-10-23
EDIT: I tested again, and before the screen turned off I was able to enter my passcode and start the computer. It started fine... Curious.

No difference. It suspends and shuts off power, but when turned back on hits the same "use keyboard to wake up" roadblock.

 cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
PCI0      S5    *disabled  no-bus:pci0000:00
HUB0      S5    *disabled  pci:0000:00:1e.0
UAR1      S5    *disabled  pnp:00:07
USB0      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *enabled   pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USB3      S3    *enabled   pci:0000:00:1d.3
USBE      S3    *enabled   pci:0000:00:1d.7
MODM      S5    *disabled 

And [http://paste.ubuntu.com/6292027/](http://paste.ubuntu.com/6292027/)

---

### Post by Toz on 2013-10-23
Can you try the following:
```
echo "UAR1" | sudo tee /proc/acpi/wakeup
```
...this should set UAR1 as enabled in /proc/acpi/wakeup. Then try to suspend and resume with the keyboard, mouse or power button. 

If it still doesn't work, try enabling all of the disabled ones:
```
echo "PCI0" | sudo tee /proc/acpi/wakeup
echo "HUB0" | sudo tee /proc/acpi/wakeup
echo "UAR1" | sudo tee /proc/acpi/wakeup
echo "MODM" | sudo tee /proc/acpi/wakeup
```
...and try a suspend/resume. Lets see what happens.

---

### Post by RCAProduction on 2013-10-23
None of that worked... I think there may be a different problem. Lately, the computer has gone to sleep (not to RAM... It's like it overloads and locks up) when it has to either do something graphically intensive, or if it requires a connection to the internet and has to be communicating more than normal. (e.g. games, videos, CDs, etc.) Most recently it shuts down for almost no reason at all. I feel that when it wakes from suspend it locks up, explaining why I can't do anything. Earlier this week I had remove my fourth memory card and clean it because it wasn't letting me start up. I thought it might be the graphics card, but I installed the proper software for it so that is doubtful. I need to stop these random lock-ups before I can truly tell if suspend is fixed. What should I do?

---

### Post by Toz on 2013-10-24
Faulty memory? Have you tried running a [memory test]("https://help.ubuntu.com/community/MemoryTest")?

Can I also see your pm-suspend log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

If pastebinit isn't installed, you can install it via:
```
sudo apt-get install pastebinit
```

---

### Post by RCAProduction on 2013-10-25
Memory is OK.

[http://paste.ubuntu.com/6300430/](http://paste.ubuntu.com/6300430/)

---

### Post by Toz on 2013-10-25
Here, summarized, is what your suspend log says:
```

Running hookInitial commandline parameters: 
Wed Oct 23 19:54:03 MDT 2013: Running hooks for suspend.
...
Wed Oct 23 19:54:05 MDT 2013: performing suspend
Wed Oct 23 19:54:22 MDT 2013: Awake.
Wed Oct 23 19:54:22 MDT 2013: Running hooks for resume
...
Wed Oct 23 19:54:24 MDT 2013: Finished.
```
So according to your log file, the computer suspended and resumed successfully. It would appear that the issue is not that the computer is not resuming, but rather when it resumes, you don't have a video output. 

From your lsmod (from the log file):
> radeon                837142  3 
...it appears that you are using the opensource radeon drivers. Have you tried enabling the proprietary fglrx drivers? They're generally better at suspending a system.

---

### Post by MrSteve on 2013-10-25
had a similar problem on my desktop computer running 12.04
the work around that worked for me was to install xscreensaver

which when started allows you to disable the gnome screen saver
(you can remove gnome screen saver if you wish)

then set xscreensaver up in the startup applications

name=xscreensaver
command=xscreensaver -nosplash

---

### Post by RCAProduction on 2013-10-25
Sorry... Enabling what? My video card IS a radeon.... I can't use the card built into the computer because it has a different cable than my monitor. When I go to settings and search for proprietary video cards, the computer says there were none (A little odd?).

Steve,

  Thanks for the suggestion!

---

### Post by Toz on 2013-10-25
> **RCAProduction said:**
> Sorry... Enabling what? My video card IS a radeon.... I can't use the card built into the computer because it has a different cable than my monitor. When I go to settings and search for proprietary video cards, the computer says there were none (A little odd?).

Steve,

  Thanks for the suggestion!

[Radeon]("http://www.x.org/wiki/radeon/") is the name of the opensource ati drivers. The proprietary drivers use the **fglrx** driver. However, I now notice that you have an R300 model - I believe ATI discontinued support for this card so you can't use proprietary drivers anyways (which explains why their not showing up under "Additional Drivers").

There is one more thing that I can think of that we can try, and that is suspend quirks. We are going to manually set a suspend quirk while manually suspending. On resume, make note if the screen comes back. There are a few of these to try (one at a time). Sorry, but its a bit of trial and error. Note, after each "sudo bash" you will be prompted to enter your password. Do so before executing the next command.

1. ```
sudo bash
pm-suspend --quirk-dpms-on
```

2. ```
sudo bash
pm-suspend --quirk-radeon-off
```

3. ```
sudo bash
pm-suspend --quirk-s3-bios
```

4. ```
sudo bash
pm-suspend --quirk-dpms-mode
```

5. ```
sudo bash
pm-suspend --quirk-vbe-post
```

6. ```
sudo bash
pm-suspend --quirk-vbestate-restore
```

Let me know if any of these resume the system correctly.

---

### Post by RCAProduction on 2013-10-26
pm-suspend --quirk-radeon-off worked perfectly. Should I bother with the others?

I think I still have the random shutdown problem, though. I am going to go check.

EDIT: The problem still persists...

---

### Post by Toz on 2013-10-26
> **RCAProduction said:**
> pm-suspend --quirk-radeon-off worked perfectly. Should I bother with the others?
No. To make it permanent, run this:
```

sudo bash 
pm-suspend --quirk-radeon-off --store-quirks-as-lkw
```
...then, in theory, it should automatically apply that quirk when you suspend normally. So, try suspending using the method that you usually use.

> I think I still have the random shutdown problem, though. I am going to go check.

EDIT: The problem still persists...
I'm not sure what else to suggest here. Perhaps it would be best to create a new thread for this random shutdown issue and have someone else help.

---

### Post by mansonfan78 on 2013-10-26
Your random shut down problem could be caused by a failing power supply - especially if suspend-to-ram causes problems on resume.  Or it could be something as simple as a loose connection.

---

### Post by os2 on 2014-07-14
> **Toz said:**
> 
1. ```
sudo bash
pm-suspend --quirk-dpms-on
```


Is there another way to invoke the dpms-on feature?
I'm using the kernel approach to directly enter standby mode though:
```
echo mem > /sys/power/state
```

Obviously if I do this then I get a blank screen on resuming from standby. But if I run ```
sudo bash
pm-suspend --quirk-dpms-on
``` then that works.

---

### Post by Toz on 2014-07-14
You can set it as default by running:
```
pm-suspend --quirk-dpms-on --store-quirks-as-lkw
```
...once, so that it is saved in the quirk database specific for your system and then run automatically here on in (under certain conditions). More info about this parameter can be found in:
```
man pm-suspend
```

---

