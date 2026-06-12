---
title: "System freezing randomly! Tried for months now.... Help me stay with linux!"
date: 2008-01-21
forum: General Help
---

### Post by qweac on 2008-01-21
Hi!

I have this huge problem with Linux and if I can't solve it very soon I have to go back to Windows, and I really don't want that, so please help me! I'm a linux noob, so if you have any suggestions, please try to explain in detail so I can understand.

Here is the situation: My system freezes randomly. It can happen as often as several times in one hour, but it can also be stable for as long as 14 days without any freezes. When the system freeze my computer locks up entirely. I can't move the mouse or use the keyboard. If I listen to music when it happens the audio starts repeating the same 0.2 second of sound that was playing in the moment of the freeze over and over again.  When the system freezes I have to shut down the entire computer with the power button to make it work again.

I have tried Ubuntu 7.04, Ubuntu 7.10, Mint 4.0 and Fedora 8.0. They all have the same problem, and I have never experienced anything like it running Windows Vista or XP on the same computer.

I have tried several different nvidia drivers, with and without Compiz Fusion, several different music players, browsers e.g. but nothing solves the problem. I'm running out of things to try now, and I'm tired of this problem since it's been bugging me since I installed linux for the first time in August. I have of course searched the internet for probably 100 hours to find a solution without any success.

This is my computer:

Zepto Znote 6214W - Laptop
Intel® Pentium&#8482; M Yonah dual2core 1.83 ghz
Nvidia Geforce Go 7600 512MB
2gb OCZ DDR2 SODIMM
7200RPM HD
PRO/Wireless 3945ABG WLAN Card - using the ipw3945 driver that is included in all the mentioned distros by default.

I have suspected that the ipw3945 driver could be the problem, but thats just me guessing. I have tried to use other drivers for the WLAN card, but I can't figure out how to do it. And yes, I have tried several guides, but I always end up with some kind of error.

I really hope that anyone here can help me!
HELP ME STAY WITH LINUX!

---

### Post by Dngrsone on 2008-01-21
If you suspect the wireless driver, then why not disable the wireless for a while and see if the problem resolves itself?

If it does, then you can concentrate on finding an alternative way of driving your wireless, otherwise it'll be time to kook somewhere else for your problem.

---

### Post by tophcito on 2008-01-21
Hi!

An idea might be to run Memtest86+ (it is one of the entries in the GRUB boot menu, that comes up when u turn on your computer). I once had random lockups with an acer laptop, and after weeks of trying to fix it, even Memtest failed, so it went back to the manufacturer for repair.

Another idea might be that your Computer is overheating, then computers tend to have all kinds of symptoms. Since powersaving, powerconsumption and cooling under Linux works quite differently (ie. less efficiently most of the time) than under windows, that might explain why you have these freezes under Linux but not under Windows.

cheers.

---

### Post by qweac on 2008-01-22
> **Dngrsone said:**
> If you suspect the wireless driver, then why not disable the wireless for a while and see if the problem resolves itself?

If it does, then you can concentrate on finding an alternative way of driving your wireless, otherwise it'll be time to kook somewhere else for your problem.

Simply because I get internet from the wireless card. The computer only freezes when I use it and it's not so much to do on it without internet. I can't be without it for like 14 days to make sure it's not the source of my problem.

> **tophcito said:**
> Hi!

An idea might be to run Memtest86+ (it is one of the entries in the GRUB boot menu, that comes up when u turn on your computer). I once had random lockups with an acer laptop, and after weeks of trying to fix it, even Memtest failed, so it went back to the manufacturer for repair.

Another idea might be that your Computer is overheating, then computers tend to have all kinds of symptoms. Since powersaving, powerconsumption and cooling under Linux works quite differently (ie. less efficiently most of the time) than under windows, that might explain why you have these freezes under Linux but not under Windows.

cheers.

i have thought of memtest before, but since it's not a problem in windows I kind of figured out that it had to be something else that caused the problem. Something in linux.

I know that my computer have overheating issues when I play games, but it causes the computer to restart and not to freeze. Also I can't see a pattern between the freezes and warmth, so it has to be something else.

Thanks to both of you for suggestions.

---

### Post by plucky on 2008-01-22
> i have thought of memtest before, but since it's not a problem in windows I kind of figured out that it had to be something else that caused the problem. Something in linux.

These operating systems handle memory errors very differently.When I first started on linux,dual booting with XP I had lots of problems with linux installation even though XP was running ok but slow.Eventually ran windows memory diagnostic and it did pull out a memory problem on one of the modules. Don't dismiss a memory problem just because windows works!!

Probably worth running memory diagnostic overnight when system not in use.To eliminate the wireless,can you use a wired connection instead? to the same modem router setup.

Good luck

---

### Post by qweac on 2008-01-22
> **plucky said:**
> These operating systems handle memory errors very differently.When I first started on linux,dual booting with XP I had lots of problems with linux installation even though XP was running ok but slow.Eventually ran windows memory diagnostic and it did pull out a memory problem on one of the modules. Don't dismiss a memory problem just because windows works!!

Probably worth running memory diagnostic overnight when system not in use.To eliminate the wireless,can you use a wired connection instead? to the same modem router setup.

Good luck

Ok, I'll run a memtest then. :)

It would be pretty difficult to do that, but I guess I could try setting up a wired connection for my laptop.

Thank you!

---

### Post by qweac on 2008-01-23
I have done some testing now, and there is nothing wrong with the memory.

I then tried to run my laptop with the wireless driver disabled. The computer still froze, so then it is not the wireless card! 

Any suggestions for what it could be? 

Oh, and in Vista, Windows reported that there was something wrong with texas instrument something, and that Windows could not use it. Could that have something to do with my freezing problems in linux?

---

### Post by Dngrsone on 2008-01-23
That is possible.  Get the hardware information and see if you can locate that TI thing.

---

### Post by Kubunteando on 2008-01-23
Can you post the kernel log file?

The full path is /var/log/kern.log

Maybe it can be seen something there.

How hard is the freezing? Does Caps Lock still flash the LED, or can you move the mouse?

By the way, I am looking Zepto as a possible laptop option,
How happy are you with it? Do you have any issues with yours?

---

### Post by qweac on 2008-01-23
The texas instrument thing seemed to have a driver and everything in Ubuntu, so I guess thats not the problem. All seemed alright in hw information.

And about my my kernel log file: I did a fresh install of Ubuntu earlier today, and I have not experienced any freezes yet, so I guess there is no use of posting it now, but I will post it right after my next freeze. :) No I can't move my mouse or anything. I do not know if the caps lock still flash the LED during freeze, but I will check next time.

I am very happy with my Zepto. The biggest problem is the one this thread is about... :P And also I have this overheating problem with mine. I have the 14" version with 7600go, and that is a pretty powerful GPU in a very small laptop, so I cannot play 3d games. I could when it was new, but not anymore. I guess it is full of dust or something! :P I know that overheating is a usual problem with the 6214W series. I do not play games on my computer anymore anyway, so I do not care about that. :P

Thanks, both of you. :)

---

### Post by Whiffle on 2008-01-23
Have you seen this page?
[http://wiki.archlinux.org/index.php/Zepto_Znote_6214W](http://wiki.archlinux.org/index.php/Zepto_Znote_6214W)

> 
Boot the kernel with noapic because the BIOS is a little buggy. This prevents random freezes when watching DVD's, gaming etc.


---

### Post by qweac on 2008-01-23
> **Whiffle said:**
> Have you seen this page?
[http://wiki.archlinux.org/index.php/Zepto_Znote_6214W](http://wiki.archlinux.org/index.php/Zepto_Znote_6214W)

No! :O that's just awesome, but what is noapic? What does it do? And how do I boot Ubuntu with noapic?

Thanks so much! I could seriously marry you if this solves my problem!

---

### Post by darryn.smith on 2008-01-23
Good day, 

My Hp laptop is rather pesky as well. 

Here's what I added to my menu.lst

You can find menu.lst here:  /boot/grub

there are many ways to edit menu.lst a simple way is to open a terminal and type 'sudo gedit /boot/grub/menu.lst' 

Look for the 1st line that looks similar to this
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5d872f0d-4a02-40bc-b43c-2730cd9f3ee2 ro splash


I personally found the splash would freeze my laptop .. not always but sometimes.. so I removed it. 


hence on the kernel line after 'ro' I appended these options:

noapic irqpoll pci=routeirq


I should point out that you can simply add these kernel options at boot. by pressing 'e' (edit) on the grub boot menu.  This method is temporary but allows you to try out different options. 

Hope I haven't left anything out..  

enjoy

---

### Post by qweac on 2008-01-23
Thank you very much! I think I found the right place. I just added noapic after "splash" since that was what the wiki said I had to use. Now I guess it's just to see what happens next... Hope it works! :)

Anyone know what noapic does? How can I check if I activated it correctly? And what are the other options you added?

Thanks again! You guys are really helpful... :D

---

### Post by darryn.smith on 2008-01-23
ACPI

Short for Advanced Configuration and Power Interface, a power management specification developed by Intel, Microsoft, and Toshiba. ACPI, which will be part of the next version of Windows, enables the operating system to control the amount of power given to each device attached to the computer. With ACPI, the operating system can turn off peripheral devices, such as a CD-ROM players, when they're not in use. As another example, ACPI will enable manufacturers to produce computers that automatically power up as soon as you touch the keyboard.  (from [http://www.webopedia.com/TERM/A/ACPI.html](http://www.webopedia.com/TERM/A/ACPI.html))

The other options I've used:

 The "irqpoll" boot parameter reduces driver initialization failures due to shared interrupts


pci=routeirq
As of 2.6.10, PCI interrupts are not routed on ACPI systems
until the device driver calls pci_device_enable().  The
"pci=routeirq" parameter restores the old behavior of
routing all the interrupts before starting drivers.

*above from blogs/email lists etc..

---

### Post by Whiffle on 2008-01-23
acpi != apic 

apic:
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by qweac on 2008-01-23
Okei, so in other words I just turned off some power saving thingy when I wrote in noapic? Will I still be able to use a cpu frequency tool? To save some power that way...?

And also, I restarted my computer a couple of minutes ago, and I got some kind of X error, so Ubuntu booted into some kind of low resolution mode (safe mode thing?). Could that have something to do with noapic? When I restarted another time everything was back to normal, so hopefully it was just that one time.

Thanks again guys! :)

---

### Post by qweac on 2008-01-25
Seems like X only starts properly around 3 out of 4 times after I turned noapic on. Why? No freezes yet...

---

### Post by danwood76 on 2008-01-25
you may need to add nolapic to the same line just after noapic to disable it fully.
not sure why it would cause x errors though.

Try this to see if it helps,
Danny.

---

### Post by qweac on 2008-01-25
> **danwood76 said:**
> you may need to add nolapic to the same line just after noapic to disable it fully.
not sure why it would cause x errors though.

Try this to see if it helps,
Danny.

Hmmm, anyone else who knows more about that? 

But why do I get these damn X fail/error things so often?

---

### Post by danwood76 on 2008-01-25
Have you tried updating your BIOS?

I notice in that arch thread that someone mentions a later BIOS being more stable and properly asserting CPU frequency scaling.

regards,
Danny

---

### Post by qweac on 2008-01-25
I have done some more testing now. I still don't know if noapic fixes the freezing problem, but when it is enabled Ubuntu only start correctly one out of two times. So if it starts one time it will not start the next time. If it didn't start last time, it will definetly start this time and so on. This is quite frustrating and I can't have a system like that. When it fails it is because of no screen or something like that. I have tried to install a fresh install of Ubuntu, but still the same problem.

Anyone who knows why I experience this strange problem?

---

### Post by qweac on 2008-01-25
> **danwood76 said:**
> Have you tried updating your BIOS?

I notice in that arch thread that someone mentions a later BIOS being more stable and properly asserting CPU frequency scaling.

regards,
Danny

Thanks, but yes, I have the latest BIOS available.

---

### Post by danwood76 on 2008-01-25
you could try running your gfx card with the vesa drivers to try and determin weather the nvidia driver is causing issues. Obviously you will have no 3d or opengl but you will be able to see if it still crashes and so on.

I have read about nvidia drivers causing problems in some systems, possibly coupled with desktop effects and so on.

regards,
Danny

---

### Post by whaase on 2008-02-02
If you are using a Nvidia driver, try this:

Open the startscript for Compiz:

sudo gedit /usr/bin/compiz


look for the line about "No indirect by default" and change it to

INDIRECT=0

---

### Post by funnypanks on 2008-02-02
this may be a weird question. but what dvd drive do u have?

---

