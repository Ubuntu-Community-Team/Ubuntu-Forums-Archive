---
title: "Laggy mouse/keyboard at a distance and monitor doesn't wake after going to sleep"
date: 2014-04-15
forum: General Help
---

### Post by I.Bun.Tu on 2014-04-15
I have two separate issues with a new PC I built, but I have a feeling they might both be related to my USB.

Here are the hardware specs:

Corsair Vengeance Pro (2x4GB) ddr3 1600mhz cl9 dimms
AMD X6 FX-6300 (6 core, 3.5ghz, 8mb cache)
Gigabyte GA-970A-D3P AM3 socket mobo
Sapphire Radeon R7 260X OC 2gb, 1150mhz clock, 6600mhz memory

I had some iommu controller issue with my mobo and had some difficulty getting Ubuntu installed and getting my USB and ethernet ports working. I resolved the issue here: [http://ubuntuforums.org/showthread.php?t=2213035](http://ubuntuforums.org/showthread.php?t=2213035)

by adding the iommu=soft protocol to the grub cmd line of the /etc/default/grub file

Now all my ports work (although my USB3 isn't transferring at ideal speed) but I'm having these two issues:

1. I'm using a wireless usb mouse/keyboard which always works perfectly fine on any other computer more than 20-30 feet or so away. On this particular computer however the mouse and keyboard work fine at a distance of less than 5 feet but if the mouse and keyboard are more than 10 feet away I get really laggy input. As in there is a delay in the input and then a hold, so with the keyboard I start typing and it's non responsive but then some letters get filled and then it gets stuck on some letters. For example if I typed 'ubuntu' into the dash or into a web search engine or w/e it would go something like: ubbbbbbbbbbbbunttttttttttttttttuuuuuuuuuuuuuuuuuuuuuuuuu

and I try to backspace some of it and it backspaces the whole thing and I can kind of get a word typed if I go letter by letter, but it's insane. I will try to record my desktop and upload a video. The weird thing is that the mouse/keyboard works fine if I'm closer than 5 feet but not if I'm further than 10. I've been using this mouse/keyboard at a distance of 10-15 feet the past year or so on a few different computers. All running Ubuntu. The mouse/keyboard combo is the Logitech Mx5500 Revolution

2. I think I'm having this exact issue that the OP never got an answer for: [http://superuser.com/questions/540918/monitor-goes-to-sleep-and-wont-wake-up](http://superuser.com/questions/540918/monitor-goes-to-sleep-and-wont-wake-up)

I have lock and suspend disabled. The monitor turns off after 30 mins. If I touch the mouse or keyboard within a few minutes of this, the monitor turns back on. I've even left the computer for a few hours and been able to get the monitor back on. Almost always when I try to get the monitor back on after leaving the computer inactive overnight, I am not able to get the monitor back on from any amount of mouse or keyboard input. What's more is that none of the USB ports seem to respond.

I would appreciate any help or advice on trouble-shooting these issues. I still have more steps to try and take to trouble-shoot problem 2 because I have to wait for it to occur. I've also read up on some similar issues that were solved by a BIOS update (including the iommu controller issue) so I'm going to try that and post back. Thanks for reading.

---

### Post by I.Bun.Tu on 2014-04-26
This issue along with a bunch of others was caused by a controller (at least iommu) issue with the AMD 970 chipset on the north bridge of certain motherboards, most notably gigabyte models. I have upgraded to a motherboard with an AMD 990FX chipset and it has solved all of my issues.

---

