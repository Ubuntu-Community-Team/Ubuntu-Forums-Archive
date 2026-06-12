---
title: "Message between GRUB and login disappears too soon"
date: 2014-04-12
forum: General Help
---

### Post by vasa1 on 2014-04-12
Each time I start my laptop running 13.10, I see a message that appears on the screen after the GRUB screen but before the login screen. It comes and goes pretty fast but it appears to be about downloading some wireless driver(?).

Is there a log file or anything else or any other way to let me see what exactly is being said?

---

### Post by vasa1 on 2014-04-13
It's in **/var/log/dmesg**:
```
[09:37 AM] /var/log $ grep "b43-phy0" dmesg
[   11.843343] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.884232] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   13.121052] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   13.121106] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   13.121144] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[09:37 AM] /var/log $ 


```

---

### Post by carl4926 on 2014-04-13
If you have a broadcom wireless device
Are you using the proprietary driver ([COLOR=#000000][FONT=Ubuntu]bcmwl-kernel-source[/FONT][/COLOR]) as opposed to b43?

---

### Post by vasa1 on 2014-04-13
> **carl4926 said:**
> If you have a broadcom wireless device
Are you using the proprietary driver ([COLOR=#000000][FONT=Ubuntu]bcmwl-kernel-source[/FONT][/COLOR]) as opposed to b43?
Thanks for responding :)

No, so far I don't have any wireless device at all but I've got an entry-level smart-phone, Samsung Galaxy Duos, and would be interested in using Bluetooth to transfer data back and forth between it and my laptop. But I will look at that possibility after 14.04 is released. I could also use the USB cable for transfer but Bluetooth seems more convenient.

I don't know anything about "drivers" or whether the one in the message or any other one is needed for Bluetooth.

I'm sure I'll need help down the road!

---

### Post by carl4926 on 2014-04-13
In part your code says ```
[COLOR=#000000][FONT=Ubuntu Mono]Broadcom 4312 WLAN found[/FONT][/COLOR]
```

Which suggest you may well have a broadcom wireless device.
During install, if you select install 3rd party software, it would install the proprietary driver 

Your device, if you actually have a broadcom device would also be supported by the b43 driver. However the firmware needs to installed in order to use it. The message you are seeing is nothing to worry about.

You could post the result of
```
[COLOR=#000000][FONT=Ubuntu]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```

---

### Post by vasa1 on 2014-04-13
> **carl4926 said:**
> In part your code says ```
[COLOR=#000000][FONT=Ubuntu Mono]Broadcom 4312 WLAN found[/FONT][/COLOR]
```

Which suggest you may well have a broadcom wireless device.
During install, if you select install 3rd party software, it would install the proprietary driver 

Your device, if you actually have a broadcom device would also be supported by the b43 driver. However the firmware needs to installed in order to use it. The message you are seeing is nothing to worry about.

You could post the result of
```
[COLOR=#000000][FONT=Ubuntu]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```

1: I'm pretty sure I selected install 3rd party software but not 100% sure. Can I tell now, at this late stage?

2: And here's the code
```
[11:08 AM] ~ $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
[11:08 AM] ~ $ 

```
My computer is a Dell 1545 Inspiron (Core2Duo) from 2009. It's working decently (except for stuff that needs hardware acceleration because the graphics is integrated).

---

### Post by vasa1 on 2014-04-13
And there's this:
```
[11:08 AM] ~ $ apt-cache policy firmware-b43-installer
firmware-b43-installer:
  Installed: (none)
  Candidate: 1:017-2
  Version table:
     1:017-2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/multiverse amd64 Packages
[11:13 AM] ~ $ 
```
Should I try
```
sudo apt-get install firmware-b43-installer
``` and see what happens?

---

### Post by vasa1 on 2014-04-13
I'm doing so now:
**b43-fwcutter firmware-b43-installer** were installed and now something is being done. I'll post that output in a while ... takes some time at 70 kB/s.

Done!
```
3 AM] ~ $ sudo apt-get install firmware-b43-installer
[sudo] password for vasa1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.9 kB of archives.
After this operation, 150 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ saucy/main b43-fwcutter amd64 1:017-2 [24.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ saucy/multiverse firmware-b43-installer all 1:017-2 [3,980 B]
Fetched 28.9 kB in 1s (25.9 kB/s)                 
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 147366 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a017-2_amd64.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a017-2_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:017-2) ...
Setting up firmware-b43-installer (1:017-2) ...
No chroot environment found. Starting normal installation
--2014-04-13 11:16:00--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: ‘broadcom-wl-5.100.138.tar.bz2’

100%[=================================>] 1,35,14,651 66.0KB/s   in 3m 7s  

2014-04-13 11:19:09 (70.4 KB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
[11:19 AM] ~ $ 

```

I'll reboot later today and see what happens! Please check this thread tommorow and so that I can have your feedback! :)

---

### Post by carl4926 on 2014-04-13
You didn't select 3rd party or the driver would be different

Although it says```
[COLOR=#000000][FONT=Ubuntu Mono]Kernel driver in use: b43-pci-bridge[/FONT][/COLOR]
```this is normal even if you never ran the firmware installer before

Have you not been using wireless? Or can you confirm that it was already working.

It's possible you used the Additional Drivers section post install and selected the b43 option rather than the 'wl' proprietary driver

IMO
b43 is better to use than the 'wl' option.

For me though, there is a bug in the kernel that makes it slower to reconnect after suspend, but it's not a great issue.

---

### Post by vasa1 on 2014-04-13
> **carl4926 said:**
> ...
Have you not been using wireless? Or can you confirm that it was already working.

It's possible you used the Additional Drivers section post install and selected the b43 option rather than the 'wl' proprietary driver

IMO
b43 is better to use than the 'wl' option.

For me though, there is a bug in the kernel that makes it slower to reconnect after suspend, but it's not a great issue.
No, I've not been using wireless at all. 

It's just this message was always showing up and so I thought to get help in case it matters when 14.04 comes around.

---

### Post by carl4926 on 2014-04-13
Once the firmware is installed, the message should go

But FYI. The firmware is located in /lib/firware/b43

I actually keep a copy of the folder /b43 on a pen drive. Because I can copy in to a live session if I like. Or if I'm installed remote from eth0, I can easily get wireless going by putting the b43 folder in to /lib/firmware

---

### Post by vasa1 on 2014-04-13
> **carl4926 said:**
> Once the firmware is installed, the message should go

But FYI. The firmware is located in /lib/firware/b43

I actually keep a copy of the folder /b43 on a pen drive. Because I can copy in to a live session if I like. Or if I'm installed remote from eth0, I can easily get wireless going by putting the b43 folder in to /lib/firmware
This is what I see in part:
```

drwxr-xr-x  2 root root    4096 Feb 13 07:40 av7110/
drwxr-x---  2 root root    4096 Apr 13 11:19 b43/
drwxr-xr-x  2 root root    4096 Feb 13 07:40 bnx2x/
drwxr-xr-x  2 root root    4096 Feb 13 07:40 brcm/
-rw-r--r--  1 root root   13388 Jan 31 18:10 carl9170-1.fw
```
The b43 folder has different permissions from all the other directories!!!
So I can't look into it!

Anyway, if it has nothing to do with Bluetooth, I shouldn't worry?

---

