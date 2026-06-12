---
title: "USB ports have stopped working overnight Ubuntu 12.04"
date: 2013-04-06
forum: General Help
---

### Post by TonyG44 on 2013-04-06
I have spent all day on the Ubuntu forums and going through google search results, and everything I have tried so far (including downgrading the kernel) has gotten me nowhere, so I figured I would post my own thread and see if maybe someone could help find a specific solution to my problem.

Basically my usb ports have simply stopped working. They will not read usb mouse or dvd drive. I also tried another mouse as well to make sure my mouse wasn't the problem. I know they are still recieving power because the laser lights up when I plug in my mouse. I simply can't get it to work. Besieds some fixes I have tried since I encountered the problem, I haven't installed any new software or anything, so I am quite baffled why they just stopped working. Any help would be appreciated.

---

### Post by matt_symes on 2013-04-06
Hi

I'll get the ball rolling for others as i am off to bed.

A full description of your hardware please.

Are the ports USB 1/2 or 3 ? Are all the ports affected ? 

Are you using a USB hub ?

Have you tried booting into a LiveCB/USB to see if the problem is still there ?

Did you switch your 'computer off/power cut/ left it running' between the times they worked and stopped working ?

What have you tried so far to fix it ?

Have you checked dmesg to see what it says ? You may want to post that here.

Kind regards

---

### Post by TonyG44 on 2013-04-06
64 bit HP Pavilion laptop
dual core Intel core 2 duo cpu T6500 @ 2.10 ghz
4gb ram
2 usb 2.0, both of which are not working.
I am not using a hub right now
Cannot boot into a LiveCD/USB because my internal dvd drive barely works, and my BIOS won't boot from a flash drive.
I did shut my computer off between when it worked and stopped working
I have tried installing an loder kernel, i have tried disabling the driver for my card reader on the blacklist, along with a few other things I have run through the terminal (I don't exactly remember everything I have tried)

attached is what I get from dmesg
[ATTACH]241046[/ATTACH]

---

### Post by ibjsb4 on 2013-04-06
With your mouse plugged in, open a terminal and enter:

```
lsusb
```

Do you see the mouse?

---

### Post by TonyG44 on 2013-04-06
I don't believe so, this is what I get

Bus 002 Device 006: ID 090c:137b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by TonyG44 on 2013-04-06
In case it helps. I have been trying to get my laptop to dual boot. I originally wanted to boot XP professional, but I could not get the drivers to slipstream properly and the instal could not find my hd. After this I decided to just install widows 7, but found my usb drives were no longer working. I did not mention this at first because it would boot fine with all usb ports funtioning properly even after the failed slipstream attempt, but now I am wondering if perhaps this was and underlying cause that just took time to manifest itself.

---

### Post by ibjsb4 on 2013-04-06
> Bus 002 Device 006: ID 090c:137b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 

I don't know what this is, do you have something else plugged in?

---

### Post by TonyG44 on 2013-04-07
I do not. i don't know what it is either, that's why I said I wasn't sure if the mouse was showing up. The brand of mouse that I have plugging in right now is called Labtec (it was a really cheap wired usb mouse at my university bookstore) and I looked at all of it's information before my previous post. It was made in china, not Taiwan, and none of the ID numbers match in any way.

---

### Post by matt_symes on 2013-04-07
Hi

This sounds like it may hardware failure or a BIOS issue. 

It could be a kernel issue but i think this is unlikely as you booted into an older kernel.

To eliminate a BIOS problem, reset your BIOS. Try this first.

Is there a BIOS update for your machine ?

What state is your CMOS battery in ?

Kind regards

---

### Post by dcstar on 2013-04-07
> **TonyG44 said:**
> In case it helps. I have been trying to get my laptop to dual boot. I originally wanted to boot XP professional, but I could not get the drivers to slipstream properly and the instal could not find my hd. After this I decided to just install widows 7, but found my usb drives were no longer working. ..........

Turn off the laptop, take the battery out for at least a minute to properly reset the hardware. Put the battery back in and see if things now "magically" work correctly.

---

### Post by TonyG44 on 2013-04-07
Taking out the battery did the trick, thanks everyone!

---

### Post by adaweawe on 2013-09-20
The wonder of modern computers. I don't know how you arrived at the suggestion to take out the battery to fix the USB ports, but this type of stuff has me so frustrated sometimes with learning about computers and computer science. Rather than a thoughtful deductive method of solving the issues, often we have to resort to "let's see what happens if I press this button."

I guess I'm just not comfortable with that type of thought process, and I end up feeling less like a scientist using the scientific process to solve problems, and instead more like a hopelessly confused monkey without much clue as to what step to proceed in and instead resort to push random buttons. 

Seriously I don't know where I would be without the Internet where people with similar confounding computer issues can troubleshoot together instead of being stuck alone.

---

