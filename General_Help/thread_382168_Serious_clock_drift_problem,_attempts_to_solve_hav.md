---
title: "Serious clock drift problem, attempts to solve have failed"
date: 2007-03-11
forum: General Help
---

### Post by rak6502 on 2007-03-11
I am new to Ubuntu, but not new to Linux or computers in general. I am totally blown away by how great Ubuntu is, except for a problem with my clock that has stumped me for days. All attempts at searching these forums and the net have brought me to solutions that have not worked.

The problem: over the course of every hour, my clock gains approximately 15 minutes. My understanding is that Linux reads the hardware clock at boot, then it keeps track of it's own time from that point forward. I have checked the hardware clock, and it is not fast. I have no time problems in Windows, and the battery is fine...this is a relatively new machine. 

For these reasons, I believe there is something going on with the kernel time keeping, and I have no idea how to resolve it. NTP is not a solution, because it can't / won't keep up with such dramatic drifting. 

Here's an interesting twist...in some of the other threads about this issue, I saw suggestions leading me to try putting this line in /boot/grub/menu.lst:

defoptions=disable_timer_pin_1 noapic noapictimer

Strangely, after a reboot, the time problem seemed to be resolved for a day or so, but then after rebooting again, I am having the same problems. I know this doesn't seem logical, but the line is still there, and apparently not solving my problem as it seemed before.

My hardware is an Athlon XP on a MSI motherboard with a nVidia chipset.

If anyone can help me, I'd appreciate it greatly. I'm excited to use this system as a server, but as we all know, a server that can't keep time is useless.

---

### Post by cmost on 2007-03-11
From where I sit, you have a couple of options:
1.  Try a different kernel.  There's a thread devoted to using Feisty's kernel in Edgy.  Check it out, or, compile your own (more of a hassle, but worth it if it solves your problem.)
2.  Reburn your ISO image and reinstall (in case the problem stems from some minor corruption in your install files.)
3.  Try installing your copy of Ubuntu in a virtual machine using Windows as a host and see what happens.  Also try Windows in Ubuntu host.  This will help rule out the hardware.

---

### Post by rak6502 on 2007-03-11
For anyone who is curious, or has similar problems, I think I resolved my own issue:

In the last post, I put options in the defoptions= line in /boot/grub/menu.lst. I did some more reading and found suggestions to put options at the end of the kernel line. I decided to try some options that I thought I had tried before, but I might have missed them.

So, at the end of the kernel line in /boot/grub/menu.lst, I added:

noapic nolapic

Problem solved, even after multiple reboots, so my fingers are crossed. Also, I am going to do a BIOS update, which has been suggested to resolve chipset issues and perhaps render those options unnecessary. Hope someone else with similar problems is helped by this.

---

### Post by crockettoo on 2007-04-13
"noapic nolapic" ... it sounds a bit like a magic spell :)

---

### Post by thebasti on 2007-04-27
> **rak6502 said:**
> Problem solved, even after multiple reboots, so my fingers are crossed. Also, I am going to do a BIOS update, which has been suggested to resolve chipset issues and perhaps render those options unnecessary. Hope someone else with similar problems is helped by this.

Hello. I have tried to do the same, but it seems that it worked only for one or two reboots. Today I noticed that my clock is drifting again. I have almost the same configuration as you, so I was wondering if this still works for you?

Also, it might be worth noticing that clock drift problem started again after I upgraded from Edgy Eft to Feisty Fawn, i.e. everything was fine under Edgy.

BTW, one of the reasons why I switched back to 32-bit Ubuntu was the fact that I couldn't fix my clock.

---

### Post by RedACE on 2007-05-17
I had the same problem except my clock was losing approximately 10-15 minutes per hour. I added the two lines that rak suggested and it worked.

17 May 13:05:40 ntpdate[6148]: adjust time server 129.100.2.12 offset 0.000055 sec
17 May 13:05:43 ntpdate[6187]: adjust time server 129.100.2.12 offset 0.000185 sec
17 May 13:05:46 ntpdate[6224]: adjust time server 129.100.2.12 offset 0.000117 sec

Only losing about one ten thousandths of a second every 3 seconds. Before the changes/reboot this was about 0.25 to 0.5 seconds every 3 seconds.

Thanks rak!

---

### Post by thebasti on 2007-05-17
I added same options to menu.lst (i.e. "noapic nolapic"), but I still have the problem - clock drifts about 10 minutes each hour.

Oddly enogh I have noticed that if I turn the computer on,  let it load to Ubuntu's login screen and then reboot it... Everything works fine. But if I login before rebooting it once the clock will drift again.

I would really like to find a way to permanently fix this as it's quite annoying. As I mentioned before, clock drift was one of the reasons why I switched back to 32-bits and it was all fine until I upgraded to Feisty.

---

