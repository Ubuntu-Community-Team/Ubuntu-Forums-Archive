---
title: "no hdmi in xrandr"
date: 2019-07-18
forum: General Help
---

### Post by spencer2 on 2019-07-18
[INDENT] 					I did an upgrade from 18.04 to 18.10 today & now my hdmi is not working.

xrandr Info:

```
xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.03*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)


```



lspci:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

```




I've tried switching between gdm3 & lightdm with reboots & still  nothing has changed. I see my video card so I don't think I need to  reinstall it but am not sure what to do. Any ideas would be greatly  appreciated: thank you. 

ps- I have tried plugging into different external sources, each with  their own cords - so its not a cord or monitor issue. It worked this  morning when I woke up; but then after rebooting & upgrading -- this  is not fixing the hdmi issue. 				It seems this is a rather common problem. The main thing I think I notice when I look through various solutions is that my hdmi is not even present in the xrandr output.

Help please
[/INDENT]

---

### Post by westie457 on 2019-07-18
Why did you upgrade, 18.10 is EOL today. [https://www.omgubuntu.co.uk/2019/07/ubuntu-18-10-end-of-life](https://www.omgubuntu.co.uk/2019/07/ubuntu-18-10-end-of-life)

You have some options:-
1) Back-up your personal files and clean install 18.04

2) Back-up your personal files and clean install 19.04

Probably better to go with option 1 as it has a longer support life.

---

### Post by spencer2 on 2019-07-18
can I just upgrade to 19? why am I 'stuck' at 18.10?

also; what does that have to do with my hdmi?

---

### Post by westie457 on 2019-07-18
You could upgrade to 19.04 however the broken part might carry over and still be broken after the upgrade.

A clean install of 18.04 or 19.04 should reset everything to working order.

You already know everything works in 18.04 and everything should work in 19.04

---

### Post by spencer2 on 2019-07-18
I don't understand why the only way to fix this is to reinstall Ubuntu. I have hundreds of gigs of data on this harddrive: Isn't there a way to reload a video card or something?

Why did the hdmi just disappear?

---

### Post by yetimon_64 on 2019-07-19
> **spencer2 said:**
> I don't understand why the only way to fix this is to reinstall Ubuntu. ...
Already explained by westie457, see the highlighted part of the post for why it is better to re-install for you now.

> **westie457 said:**
> You could upgrade to 19.04 however **the broken part might carry over** and still be broken after the upgrade.

A clean install of 18.04 or 19.04 should reset everything to working order.

You already know everything works in 18.04 and everything should work in 19.04
> **spencer2 said:**
>  ...I have hundreds of gigs of data on this harddrive: Isn't there a way to reload a video card or something?

Why did the hdmi just disappear?         
It probably could be looked at BUT your version is now "end of life". Why try to insist on fixing a problem on an installation that is now due for upgrading (not recommended as per the quote from westie457) or reinstalling. Doing so is pretty much a waste of time. There is a requirement on this forum  when asking for help that you are running a currently supported release, 18.10 is now not supported, your timing with the upgrade is unfortunate.

I suggest you do a backup of the "hundreds of gigs of data on this harddrive" and do a reinstall of 18.04; 18.04 is supported for 5 years till April 2023, 19.04 is only supported for 9 months till January next year. You can choose either but in my opinion 18.04 is a smarter choice for the longer support period.

Regards, yeti.

---

### Post by spencer2 on 2019-07-19
I upgraded to 19.04 & I'm still having the same hdmi problem. Is there not a way to add hdmi back into the xrandr?

The reason that I upgraded was because my hdmi has been on & off for a couple weeks now. It was fixing itself by using the gdm3 to lightdm work around but then stopped working --- hence the upgrade. 

I'm not trying to be annoying but can someone explain to me why there is not a fix for the xrandr issue?
Is there any idea as to what &/or why this issue has suddenly happened?
If there is a recurring issue with 18.04 & the hdmi; would the fresh install just be setting me up to repeat this hdmi issue again?

I do appreciate the assistance: i just wish I had more explanation or more steps that I could try before just wiping my whole hard-drive please

---

### Post by CatKiller on 2019-07-19
> **spencer2 said:**
> The reason that I upgraded was because my hdmi has been on & off for a couple weeks now. It was fixing itself by using the gdm3 to lightdm work around but then stopped working --- hence the upgrade. 

Your upgrades are a red herring, and your change of display manager was likely a placebo.

Flaky connector that's given up the ghost would be my assessment based on what you've said.

---

### Post by spencer2 on 2019-07-19
So: I have a partitioned drive -- logged into my other partition: have 18.04 lts: have run all the updates & I have the exact same issue. No hdmi in xrandr.

If my hdmi connector suddenly gave out: would it still be on lspci?

Here's the output:

lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 30)

---

### Post by spencer2 on 2019-08-01
I did the full 18.04 re-install over the weekend & for most of the week everything has been working fine --- but then I turned on my laptop this morning & I'm again without an external monitor & no hdmi listed in my xrandr.

Why am I back at this point again? What is up with 18.04 & this hdmi issue? why does xrandr keep losing my hdmi?

---

