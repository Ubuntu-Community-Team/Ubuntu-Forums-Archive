---
title: "Total system freeze in 20.04"
date: 2021-01-27
forum: General Help
---

### Post by WB0HYQ on 2021-01-27
Often enough to me irritating, version 20.04 of Ubuntu (running XFCE), will come to a complete and absolute halt. Nothing works. The mouse/keyboard has no response at all. The only solution is to use the power switch to kill everything and start over. This did not happen in 18.04.

I've checked the power supply (running at around 75% output), RAM (numerous times), heat (well within norms-including the video card), and all the logs (which show nothing out of the ordinary). I have noticed it seems to happen more often when I am either plugging in or removing a USB drive OR when I open/close Thunar.

Does anyone have any ideas on this?

Bill

---

### Post by &amp;KyT$0P# on 2021-01-27
Has this always happened on this machine as long as it's had 20.04?  Or did it start when something major was updated, e.g. kernel or graphics driver?

What kernel version is this system running?  You can find it by running in Terminal
```
uname -a
```

---

### Post by WB0HYQ on 2021-01-27
Yes. Within two hours of installing on this machine (this is a desktop, but I have it on three others - all laptops) it froze on me.

uname -a results: Linux bill-UBU 5.4.0-65-generic #73-Ubuntu SMP Mon Jan 18 17:25:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Bill

---

### Post by WB0HYQ on 2021-01-28
Can anyone else shed some light on this?

Bill

---

### Post by T6&amp;sfpER35% on 2021-01-28
also on 20.04 xubuntu with [COLOR=#000000]5.4.0-65-generic kernel and also noticed lately more and more freezes .[/COLOR]
[COLOR=#000000]i've just reckoned maybe it's cause of my OLD pc , but now i'm not so sure anymore. [/COLOR]
[COLOR=#000000]what i usually do when it freezes is hit ctrl + alt+ F1 , type username/password and type reboot . (never liked switching of pc by power switch)

sorry i don't have a cure , i'm also looking for one now lol[/COLOR]

---

### Post by WB0HYQ on 2021-01-28
In my case, the entire computer locks up. Nothing works. The keyboard is completely dead. No key combinations work at all. I did change the "power switch" action from "do nothing" to "power down." Now, when it locks up, I just touch the power switch and the computer will respond by powering down cleanly. That's the best I can do.

Bill

---

### Post by T6&amp;sfpER35% on 2021-01-28
> [COLOR=#000000]Has this always happened on this machine as long as it's had 20.04?[/COLOR]
nope ,had 20.04 for awhile now but freezes only started recently
> [COLOR=#000000]when something major was updated, e.g. kernel or graphics drive[/COLOR]
maybe , not sure , i usually don't pay much attention to what exactly gets updated ( i know , my bad ) 

*sorry if this is hijacking a thread , but seems we have the same problem*

---

### Post by T6&amp;sfpER35% on 2021-01-28
> [COLOR=#000000]In my case, the entire computer locks up. Nothing works[/COLOR]
oh yes , you said that in 1st post , sorry 
in my case at least my mouse&keyboard still works ,just the screen freezes i can click anywhere on it but nothing will happen

---

### Post by WB0HYQ on 2021-01-28
Do you use an NVIDIA driver? I had to change from NVIDIA ro Nouveau X-org driver because my screen would lock up just as your did. Keyboard/Mouse worked, but clicking did nothing. It appears we might have the same problem, especially if you are using the NVIDIA driver.

Bill

---

### Post by T6&amp;sfpER35% on 2021-01-28
yes i use the NVIDIA driver (cause it says it's recommended) . I'll switch to the Nouveau X-org driver and see if it freezes again .
Thanks !

---

### Post by T6&amp;sfpER35% on 2021-01-28
ok changing to the Nouveau driver didn't go well , now movies / videos won't play in SMPlayer ( 1st thing i noticed , didn't try other things)
switched back to NVIDIA

[ATTACH=CONFIG]287852[/ATTACH]

---

### Post by WB0HYQ on 2021-01-28
I see you're running a GeForce 210. That's a pretty old card from around 2009. Could be the X-org driver doesn't support it. This could also be the reason the more up-to-date NVIDIA driver (340.108) isn't working well either.

Bill

---

### Post by T6&amp;sfpER35% on 2021-01-29
yea i know , its an old system. hence i 1st put the freezes down to that .
ques i'll just live with it lol doesn't happen too often at the moment

---

### Post by WB0HYQ on 2021-01-29
That could be the problem with my freezes, but I'm not convinced. My system is old, yes, but two years ago I completely rebuilt it inside the old frame with just about everything new from the motherboard outward. There is the additional evidence that I never had a freeze using 12.04, 16.04, and 18.04. Only when I upgraded to 20.04 did the freezes begin. I suppose it is possible that 20.04, somewhere, in one of the hundreds of libraries, there is one bit of code that, when it runs, will cause the CPU to choke on an instruction it can't handle.

The computer is also dual-boot: Ubuntu running XFCE and Windows 7. I agree Windows 7 is old and unsupported, but it also hasn't locked up like 20.04.

Bill

---

### Post by WB0HYQ on 2021-02-06
Just now recovered from yet another freeze. Was doing nothing. The screensaver was on. When i moved the mouse, the screensaver quit and the pointer moved around the screen, but everything locked up the instant I clicked on the Cairo Dock. Had to use the power switch (now set up to "shutdown" when pressed) to recover.

Whatever it is, it's persistent and doesn't get logged. anywhere.

Bill

---

### Post by WB0HYQ on 2021-02-07
And now, nine hours later, Thunar refuses to do anything. The rest of the windows are working properly, but when I went to close Thunar, it wouldn't respond other than to cause "this window is not responding, etc.etc.etc." I can move Thunar's window around, but I can't close, resize, or do anything inside it.

Sure would like to know what's going on here. I never had these problems with any version of Ubuntu lower than 20.04. If this keeps up, I may revert back to 18.04.

Bill

---

### Post by WB0HYQ on 2021-02-18
In the last week, three more freezes have occurred. Still not a thing in any logs I can access. I pretty sure it is tied somehow to Thunar. Unfortunately, I can't remove Thunar because of the feature it offers for file/directory handling and network communications. I've checked video card temps/cleanliness and blew all the dust out of the fins for the CPU. Wasn't much, but it didn't seem to help anyway.

Is there nobody else having this problem? Hard to believe.

Bill

---

### Post by ajgreeny on 2021-02-18
No, I've never really seen this in my eight or nine years of using Xubuntu, right through from 12.04 to 20.04.
It has been just about the most stable OS I've ever used, much better than Ubuntu on my hardware which tends to be pretty much average; now nearly 8 years old with an Intel i5-3750K cpu and also using the integrated Intel graphics, no nvidia in my hardware.

I note you said Ubuntu with Xfce; does that mean you do not install Xubuntu?  If so I wonder if that has any bearing on the problem; I don't know why it should but just thinking out loud (actually in print, but I'm sure you know what I mean).

---

### Post by dragonfly41 on 2021-02-18
Does your system freeze when running LiveUSB in "Try Ubuntu" mode and then using Thunar?
Leave it running for some time.

---

### Post by DuckHook on 2021-02-18
My recent freezes were in a server running Nextcloud within a LXD container. Much different setup than yours, but 20.04 as well.

It motivated me to install monitoring SW: [this thread]("https://ubuntuforums.org/showthread.php?t=2457994").

Here are a few things it may be useful to look into:

[list=1]
[*]I know you said the logs show nothing, but with the advent of systemd, we can't just look at the old logs like *syslog* and *kern.log*. Forgive my presumption in mentioning this, but make sure you also go through *journalctl* especially: ```
sudo journalctl -p err
```
[*]Mine hinted at an instability in ZFS before the crash locked everything up completely. Yours will likely be something different, but do have a peek at that first.
[*]I felt I had nothing to lose so installed the hwe stack. So far, the new 5.8 kernel series is running okay, but like you, the freezes were intermittent and sometimes two weeks would go by with no issues. Hence, I don't really know yet if the new kernel stabilizes things.
[*]Do you have any resource&#8209;intensive processes running like I did with ZFS?
[*]Consider running both a *memtest* overnight and *fsck*.
[*]Consider running on all disks: ```
sudo smartctl -t long /dev/sd[X]
```
[/list]
I like dragonfly41's suggestion to run a LiveUSB for an extended period. It may eliminate HW as the cause.

ajgreeny also brings up a very good point. Please describe in more detail for us the general properties of your box, esp customizations (both HW and SW) and what services/modules/daemons you are running on it.

---

### Post by WB0HYQ on 2021-02-18
> **dragonfly41 said:**
> Does your system freeze when running LiveUSB in "Try Ubuntu" mode and then using Thunar?
Leave it running for some time.

No. I haven't tried that. The freezes happen spaced so far apart it would be impractical to run with a DVD for any length of time.

Bill

---

### Post by WB0HYQ on 2021-02-18
> **ajgreeny said:**
> No, I've never really seen this in my eight or nine years of using Xubuntu, right through from 12.04 to 20.04.
It has been just about the most stable OS I've ever used, much better than Ubuntu on my hardware which tends to be pretty much average; now nearly 8 years old with an Intel i5-3750K cpu and also using the integrated Intel graphics, no nvidia in my hardware.

I note you said Ubuntu with Xfce; does that mean you do not install Xubuntu?  If so I wonder if that has any bearing on the problem; I don't know why it should but just thinking out loud (actually in print, but I'm sure you know what I mean).

I've been using Ubuntu with Xfce on LTS versions from 10.04 to 18.04 and have had NO freezes at all. Only after I upgraded from 18.04 through 19.04 to 20.04 have they started. It could be something didn't get updated properly, that's true, but I'm not sure.

I have also switched from the NVIDIA driver to X.Org and back several times. This didn't stop the freezes either.

Bill

---

### Post by WB0HYQ on 2021-02-18
> **DuckHook said:**
> My recent freezes were in a server running Nextcloud within a LXD container. Much different setup than yours, but 20.04 as well.

It motivated me to install monitoring SW: [this thread]("https://ubuntuforums.org/showthread.php?t=2457994").

Here are a few things it may be useful to look into:

[LIST=1]
[*]I know you said the logs show nothing, but with the advent of systemd, we can't just look at the old logs like *syslog* and *kern.log*. Forgive my presumption in mentioning this, but make sure you also go through *journalctl* especially: ```
sudo journalctl -p err
``` 
[*]Mine hinted at an instability in ZFS before the crash locked everything up completely. Yours will likely be something different, but do have a peek at that first. 
[*]I felt I had nothing to lose so installed the hwe stack. So far, the new 5.8 kernel series is running okay, but like you, the freezes were intermittent and sometimes two weeks would go by with no issues. Hence, I don't really know yet if the new kernel stabilizes things. 
[*]Do you have any resource&#8209;intensive processes running like I did with ZFS? 
[*]Consider running both a *memtest* overnight and *fsck*. 
[*]Consider running on all disks: ```
sudo smartctl -t long /dev/sd[X]
``` 
[/LIST]
I like dragonfly41's suggestion to run a LiveUSB for an extended period. It may eliminate HW as the cause.

ajgreeny also brings up a very good point. Please describe in more detail for us the general properties of your box, esp customizations (both HW and SW) and what services/modules/daemons you are running on it.

The 'journalctl' call returned over 35,000 entries. It wasn't until I paged all the way to the bottom to get today's entries. In the midst of some "folder .... not found" entries was this gem:

```

Feb 18 17:22:15 bill-UBU kernel: nouveau 0000:01:00.0: gr: TRAP ch 3 [007fad5000 Xorg[932]]
Feb 18 17:22:15 bill-UBU kernel: nouveau 0000:01:00.0: gr: GPC0/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 3e0009 [ILLEGAL_INSTR_ENCODING]
Feb 18 17:22:19 bill-UBU kernel: nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Feb 18 17:23:04 bill-UBU pulseaudio[251660]: GetManagedObjects() failed: org.freedesktop.systemd1.ShuttingDown: Refusing activation, D-Bus is shutting down.
-- Reboot --
Feb 18 17:24:29 bill-UBU kernel: sd 6:0:0:0: [sdd] No Caching mode page found
Feb 18 17:24:29 bill-UBU kernel: sd 6:0:0:0: [sdd] Assuming drive cache: write through


```

With D-bus shutting down, there's my freeze! And, at the right time as well. Did my machine try to go to warp speed and fail? (LOL) I don't understand WHY it failed, but apparently pulseaudio was involved.

Can I delete any or all of this journal to get it back to manageable size?

Bill

---

### Post by DuckHook on 2021-02-18
> **WB0HYQ said:**
> Can I delete any or all of this journal to get it back to manageable size?
I wouldn't want to monkey with any existing log directly, but here's how you manage the journal: [https://www.certdepot.net/rhel7-get-started-systemd/](https://www.certdepot.net/rhel7-get-started-systemd/)

This is the resource that I rely on when trying to decipher systemd (of which journald is a child process). About ¼ of the way down are where the various options for reading the journal start. At bottom of that section are instructions for modifying journald.conf to limit journal size. I believe the setting you are looking for is *SystemMaxUse*.

As for the cause of your problem:

My websearch-Fu appears to be on strike today. Nothing helpful showing up I'm afraid.

All I can think of is going to HWE stack, but that's sorta like swatting a fly with a sledgehammer.

Perhaps others have seen something like this before…

---

### Post by DuckHook on 2021-02-18
Wait a minute&#8230;

Dredging up a problem/solution I ran into last year after ](*,) with pulseaudio, this may be worth a try:

[https://www.mind-overflow.net/post/how-to-reset-pulseaudio-and-alsa-on-ubuntu/#the-very-simple-process](https://www.mind-overflow.net/post/how-to-reset-pulseaudio-and-alsa-on-ubuntu/#the-very-simple-process)

---

### Post by WB0HYQ on 2021-02-18
> **DuckHook said:**
> I wouldn't want to monkey with any existing log directly, but here's how you manage the journal: [https://www.certdepot.net/rhel7-get-started-systemd/](https://www.certdepot.net/rhel7-get-started-systemd/)

This is the resource that I rely on when trying to decipher systemd (of which journald is a child process). About ¼ of the way down are where the various options for reading the journal start. At bottom of that section are instructions for modifying journald.conf to limit journal size. I believe the setting you are looking for is *SystemMaxUse*.

As for the cause of your problem:

My websearch-Fu appears to be on strike today. Nothing helpful showing up I'm afraid.

All I can think of is going to HWE stack, but that's sorta like swatting a fly with a sledgehammer.

Perhaps others have seen something like this before&#8230;

Interesting. I ran the 'size' command and was informed I was taking up 1.85G of space. So I ran the 'vacuum-size' and 'vacuum-time' commands and set it to "10M" and "14day". Now I'm down to 24M.

Now I have something a little more manageable. Thanks for the info. It's now in my "Ubuntu Stuff I Need To Know" file.

I think I can figure out what's happening now that I have a good log to take a peek at whenever it happens. I think the pulseaudio was a false scent, though. It could be that pulseaudio was the first thing to try to do anything once the trigger was set to halt the system.

Bill

---

### Post by DuckHook on 2021-02-18
Chasing down freezes is a notoriously hard and nasty business.

Good Luck!

---

### Post by dragonfly41 on 2021-02-19
Revisiting case clues:


post#1
I have noticed it seems to happen more often when I am either plugging in or removing a USB drive OR when I open/close Thunar.

post#3
Within two hours of installing on this machine (this is a desktop, but I have it on three others - all laptops) it froze on me.

post#7
had 20.04 for awhile now but freezes only started recently

post#14
There is the additional evidence that I never had a freeze using 12.04, 16.04, and 18.04. Only when I upgraded to 20.04 did the freezes begin.

and

The computer is also dual-boot: Ubuntu running XFCE and Windows 7. I agree Windows 7 is old and unsupported, but it also hasn't locked up like 20.04.

post#15
When i moved the mouse, the screensaver quit and the pointer moved around the screen, but everything locked up the instant I clicked on the Cairo Dock.

post#16
Thunar refuses to do anything. 



From the above I assume (from post#3) that Ubuntu 20.04 only freezes on desktop and not on your "three other laptops".

In post#14 you write that you "upgraded" to Ubuntu 20.04.
Have you tried a fresh install but copying files into your fresh installation (not an upgraded from old 18.04)?

Although you have a LiveDVD you could buy a reasonable size but low cost SanDisk USB flash drive to create a LiveUSB.  I would create it as persistent. There are tutorials for this. You can use mkusb from within Ubuntu.

Then either in your freezing host or in the LiveUSB (not LiveDVD) you can use an automation script as a "test bed" to stress test your desktop.

My favourite utility for this is Actiona which, although using very dated Qt4 objects and Actionscript2, I find to be very useful in writing UI automation scripts.  Another useful automation tool is xdotool (but without a GUI).

I can offer some more UI automation tips if you go down this path. Actiona is ingrained into almost every automation task I develop.  It is rather like the old clicompanion.

Another useful Linux monitoring tool to install is Stacer.

---

### Post by WB0HYQ on 2021-03-10
My apologies, Dragonfly. I was not notified anyone had answered my last post. You gave me quite a bit to think about, and I'll investigate the tools you mentioned.

Since two weeks ago, I've been frozen three more times. All of them indicate the DBUS in some manner or other. Log entries state "unknown error", then "Halting DBUS", then "Not restarting DBUS". This means nothing works: no keyboard or anything else. I've programmed the Power switch to cause a normal shutdown and that, at least, works so I can shutdown properly. I can't for the life of me figure out what is causing these DBUS failures.

Bill

---

### Post by MartyBuntu on 2021-03-10
Try running memtest (the long test). It won't cost you anything.

---

### Post by WB0HYQ on 2021-03-11
Good idea. As you say, it can't hurt. I replaced the original memory modules (4G each) with 8G Hyper-X modules a year ago. i suppose one could have gone wonky.

Bill

---

### Post by WB0HYQ on 2021-03-11
Well, that was enlightening. Every test I ran looked good until it reached 30%. Then, it either froze, or rebooted. I ran some specific tests, such as random numbers, or patterns. They either got to 30% and blew up, or never made it that far. The bad spot seemed to be near the "bottom" of RAM in the lowest 2G range when it faltered. It appears I have a bad module. I'll have to replace both of them just to make sure I get the right one. Two years is not a good track record though.

I guess the OS has a fairly robust RAM paging system in place to fail only occasionally. As an author, some of my projects have a lot of windows/applications open or running at the same time.

Thanks for the advice, Martybuntu.

Bill

---

### Post by WB0HYQ on 2021-03-11
I swapped the two RAM modules around. When I ran the test again, it failed at exactly the same spot: 30% and the Address was nearly the same (in the same testing block of 2G). **I need a little bit of advice now**. Does this indicate a bad RAM module, or could it be something on the motherboard? I'm not at all sure how RAM is addressed electrically as well as by the OS. What is strange is I have Windows as dual boot and it has never frozen--at least the times I've run it.

I'm tempted to go ahead and buy two new RAM modules. but would hate to go the expense if it might be something elsewhere, such as the motherboard. That, I can't replace as it in itself IS already a replacement from an older board. The box is ten years old, motherboard six, RAM modules two. It is truly a frankenmonster.

Bill

---

### Post by CelticWarrior on 2021-03-11
In such cases it's more likely a problem with the VRAM (graphics card) and not system's RAM.

---

### Post by dragonfly41 on 2021-03-11
Last chance saloon.
You might try cleaning the edge connectors of RAM cards with a clean rubber ,, gently and carefully, having earthed yourself first to avoid static.

Then try reseating the cards one at a time (rebooting each time). Then both. 

 That is:
 remove both cards A & B to clean edges
insert **only **card A -> reboot to test
shutdown after testing

remove card A
insert **only** card B-> reboot to test
shutdown after testing

reinsert card A (so you now have **both** A and B inserted)
reboot to test

---

### Post by hk42 on 2021-03-12
Sometimes RAM problems are due to their driver chip.
Mine was overheating because the big ,fat, rubber like piece between it and 
his otherwise rather cool radiator.
The windows software HWINFO spotted the problem that existed only
when the two RAM slots were populated.

---

### Post by WB0HYQ on 2021-03-12
> **CelticWarrior said:**
> In such cases it's more likely a problem with the VRAM (graphics card) and not system's RAM.

I wish this site still notified people when there was a reply to a thread. Made things much easier.

I wondered about this so I temporarily replace my video card with an older model and ran memtest again. Still failed at the same spot. Good idea, though.

Bill

---

### Post by WB0HYQ on 2021-03-12
> **dragonfly41 said:**
> Last chance saloon.
You might try cleaning the edge connectors of RAM cards with a clean rubber ,, gently and carefully, having earthed yourself first to avoid static.

Then try reseating the cards one at a time (rebooting each time). Then both. 

 That is:
 remove both cards A & B to clean edges
insert **only **card A -> reboot to test
shutdown after testing

remove card A
insert **only** card B-> reboot to test
shutdown after testing

reinsert card A (so you now have **both** A and B inserted)
reboot to test

I did this about an hour ago. Same results. I am leaning heavily to a problem on the motherboard now. One of the chip drivers may be faulty.

Bill

---

### Post by WB0HYQ on 2021-03-12
> **hk42 said:**
> Sometimes RAM problems are due to their driver chip.
Mine was overheating because the big ,fat, rubber like piece between it and 
his otherwise rather cool radiator.
The windows software HWINFO spotted the problem that existed only
when the two RAM slots were populated.

My chips sit right in the airstream from the exit fan at the back of the cabinet. I am unable to see the RAM module boards themselves because the manufacturer has put a shield over the whole thing. I blew on it with air while running the test. Same result.

I've also run several temperatures applications, but only one of them gave me the temp of the RAM chips. It seemed "normal" if there is such a thing.

Bill

---

### Post by WB0HYQ on 2021-03-12
Just now ordered a new set of chips. When I checked on my Amazon back orders, I found I was wrong about when I bought these modules. It was 2017, not 2019, so that would make them 4 years old. I have another desktop in my server room that could use a RAM upgrade, so if these new chips prove there is a fault on the motherboard, I'll use them in that box and retire this one. Luckily, my entire Ubuntu install is on an internal 1TB drive I can just swap into the other box and be back up right away.

Bill

---

### Post by WB0HYQ on 2021-03-13
@Dragonfly41: To be more specific about the results of the test you outlined, when I plugged in just one of the modules (in either slot, DIMM1 or DIMM2) the test ran to 61% then failed each time, on each module, in either slot. This, to me, indicates a motherboard problem. The default test was "own address parallel." Other specific tests failed at different percentages, but none of them made it all the way through to 100%.

Bill

---

### Post by dragonfly41 on 2021-03-13
I tend to agree with your diagnosis. But some more reading matter ..

[https://www.memtest86.com/tech_individual-test-descr.html](https://www.memtest86.com/tech_individual-test-descr.html)

[https://www.computerhope.com/issues/ch001089.htm](https://www.computerhope.com/issues/ch001089.htm)

> "Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth".

                                              Arthur Conan Doyle

---

### Post by WB0HYQ on 2021-03-13
What I forgot to add before was I received my new modules this morning. neither one of them passed either and I KNOW they are good as they pass in another computer. incidentally, so did the original modules. Something I should have done right away was swap the "failing" modules into the other box. Shrug.

Good references.

Bill

---

### Post by CelticWarrior on 2021-03-13
Again, try swapping the graphics card if you have one available or just use the iGPU - if available - for the purpose of testing the memory.
Memory test software test both VRAM, the graphics card own RAM, and the system's RAM (if using iGPU only it tests only the system's RAM, of course). The errors you're experiencing consistently at the same point (~30% with 2 modules and ~60% with only one, irrespective of the modules being tested and in what order) strongly suggest the problem is in the graphics card, not in the system's memory.

---

### Post by WB0HYQ on 2021-03-13
Did that this afternoon. The situation remains the same regardless which graphic card I use. My normal card is an NVIDIA GT710 (Yes, I know it's old) and I temporarily replaced it with an even older GT220. I'm afraid the MOBO is a goner.

Bill

---

### Post by CelticWarrior on 2021-03-13
> **WB0HYQ said:**
> Did that this afternoon. The situation remains the same regardless which graphic card I use. My normal card is an NVIDIA GT710 (Yes, I know it's old) and I temporarily replaced it with an even older GT220. I'm afraid the MOBO is a goner.

Bill

That being the case I must agree with you.

---

### Post by WB0HYQ on 2021-03-13
Darn shame, too. The case is only 12 years old. Internally, it's been gutted and replaced a lot of times. A true Frankenmonster.

Bill

---

### Post by CelticWarrior on 2021-03-13
The motherboard might need recapping.

---

### Post by bcschmerker on 2021-03-13
> **WB0HYQ said:**
> I see you're running a GeForce 210. That's a pretty old card from around 2009. Could be the X-org driver doesn't support it. This could also be the reason the more up-to-date NVIDIA driver (340.108) isn't working well either.

Bill
**I've a related, not identical, issue with an *e*machines®/ac*e*r® EL1210-09** (Acer Computer DAO78L: 2.4 GHz Advance Micro Devices® Athlon 64® LE-1620; nVIDIA® MCP78 northbridge (with C77 64-bit *geForce*® GPU) and MCP72 I/O hub), and I want the planar C77 only for kernel reporting, as I've already retrofitted a *msi*® N610GT-1GD3-LP video display adapter (nVIDIA® GF119) that is currently supported for primary and secondary displays.  I found the nvidia-340-dkms driver buggy, the libnvidia-*-390 and linux-modules-nvidia-390-*-generic packages stable; may have to open a new Thread for booting with both GPUs for their specifc purposes.  Wouldn't be surprised if nvidia-340 is a WontFix.

---

### Post by lordgallen on 2021-03-13
Would you consider re-installing 18.04 to see if it's working the way it should, or like before, and then re-installing 20.04, maybe something occurred during the first install. How about giving it another shot, to be sure that it's not hardware related?

---

### Post by daniewicz on 2021-03-13
Do you know how to clear the CMOS on the motherboard? There should be two pins you can short.

---

### Post by daniewicz on 2021-03-14
This has been known to fix a misbehaving motherboard.

---

### Post by WB0HYQ on 2021-03-17
Sorry. **Once again the email system has failed to notify me of a response.**

> **lordgallen said:**
> Would you consider re-installing 18.04 to see if it's working the way it should, or like before, and then re-installing 20.04, maybe something occurred during the first install. How about giving it another shot, to be sure that it's not hardware related?

I ran a live session from CD and, yes, it did fail after about three hours of surfing the web and other RAM intensive activities. So, my estimation is the RAM driver chip(s) failed about the time I upgraded--maybe even at the same time.

Bill

---

### Post by WB0HYQ on 2021-03-17
> **daniewicz said:**
> Do you know how to clear the CMOS on the motherboard? There should be two pins you can short.

Yes, I do. But according to the extensive testing I've done, there are actually TWO address lines rising when only one should be selected. According to the o-scope, the second (erroneous) address line is coming up as a spike and not a square wave.

Definitely a bad driver chip.

Bill

---

### Post by bcschmerker on 2021-03-20
> **WB0HYQ said:**
> I swapped the two RAM modules around. When I ran the test again, it failed at exactly the same spot: 30% and the Address was nearly the same (in the same testing block of 2G). **I need a little bit of advice now**. Does this indicate a bad RAM module, or could it be something on the motherboard? I'm not at all sure how RAM is addressed electrically as well as by the OS. What is strange is I have Windows as dual boot and it has never frozen--at least the times I've run it.

I'm tempted to go ahead and buy two new RAM modules. but would hate to go the expense if it might be something elsewhere, such as the motherboard. That, I can't replace as it in itself IS already a replacement from an older board. The box is ten years old, motherboard six, RAM modules two. It is truly a frankenmonster.

Bill
**Two LTS cycles ago, I had random crashes in the Hot Rod gPC, traced it to a bad MPU.**  The Advance Micro Devices® Athlon64® Series (AMD MPU generation K8) was the first desktop MPU to pack an on-die memory manager; int[sub]e[/sub]l® followed suit with the Core Processor series (starting with the 1st-Gen Core, FCLGA 1156).  Intel Corporation and Advance Micro Devices use different approaches to the MMU, as the Core Processor Series (FCLGA 1156, 1155, 1150, 1151, 1200) and Core Processor-X Series (FCLGA 1366, 2011, 2011v3, 2066) uses different IOMMU kernel procedures from the Sempron/Athlon/Phenom (Sockets AM2b, AM3, AM3b, FM1, FM2, FM2b, AM4).  I'm currently preparing a hunt for an AMD Athlon 64 BE-2450 (2 CPUs, 200 MHz x 12.5; Socket AM2 - P/N ADH2450IAA5DO) for the *e*machines®/ac*e*r® EL1210-09 that I'm preparing for projection duty at OMS Japanese Christian, and an Athlon II® X4 630 (4 CPUs, 200 MHz x 14; Socket AM2b - P/N ADX630WFK42GI) for the ASUS® CM1630 currently running Win 10; the Athlon II® X2 220 (2 CPUs, 200 MHz x 14; Socket AM2b - P/N ADX220OCK22GI) currently in the CM1630 will go into the Hot Rod, once I've a new planar.

---

### Post by wisjim2 on 2021-03-22
I have a similar problem when using thunar file manager. only it more than locks up. it totally logs out and I lose all work. No warning. Just blank screen then login screen. I'm trying a different manager. It only happens when I'm working with the file manager which in this case happens to be thunar.

---

### Post by WB0HYQ on 2021-03-23
Thunar has done this to me several times as well. Tosses me right off the system. No halts, but I'm back to the login screen almost immediately. But, this is off-topic for this thread.

Bill

---

### Post by vmpx on 2021-03-26
I have the same problem on 20.04 and not on 18.04 or 16.04.
nvidia GEFORCE GT730 Silent 2GB DDR3 from ASUS
nouveau driver

---

### Post by WB0HYQ on 2021-03-26
> **vmpx said:**
> I have the same problem on 20.04 and not on 18.04 or 16.04.
nvidia GEFORCE GT730 Silent 2GB DDR3 from ASUS
nouveau driver

Have you narrowed it down to mis-addressed RAM chips on the motherboard?

Bill

---

### Post by vmpx on 2021-03-26
Result of Memtest86+
Pass: 1 Errors: 0

---

### Post by WB0HYQ on 2021-03-26
Then you don't have the same problem. I cannot get through memtest once without  failure at around either 30% or 62%, depending on how many memory modules I have installed. I'd suggest maybe starting another thread listing your specific problem and the measure you've taken to solve it.

Bill

---

### Post by bcschmerker on 2021-03-26
> **WB0HYQ said:**
> Then you don't have the same problem. I cannot get through memtest once without  failure at around either 30% or 62%, depending on how many memory modules I have installed. I'd suggest maybe starting another thread listing your specific problem and the measure you've taken to solve it.

Bill
**Does your system pack an intel® Core Processor&#8482; (FCLGA 1156, 1155, 1150, 1151, 1200, 1366, 2011, 2011v3, or 2066); or an AMD® Athlon 64® or later (Socket AM2/+, AM3/+, FM1/+. FM2/+, or AM4)?**  The memory manager is on the die for these MPU's.  Two LTS cycles ago, I was tripped up by a memory manager failure.  Swap out the MPU to rule out a memory-management-unit failure.

---

### Post by vmpx on 2021-03-27
>  I cannot get through memtest once without  failure at around either 30%  or 62%, depending on how many memory modules I have installed.
You can first prove only two memory modules. If they are ok you can remove them and prove the next two ones until you get an error. The faulty one can you remove. In the end you can only use good memory modules in a computer.

---

### Post by vmpx on 2021-03-27
In User Guide of my motherboard:
> 
Always install DIMMs with same CAS latency.
Due to chipset limitation, this motherboard can only support up to 8 GB on the operating systems listed below.
You may install a maximum of 2 GB DIMMs on each slot.
Qualified Vendors Lists (QVL) DDR3-1333MHz capability:
Size/Vendor/Part No./SS(Single-sided)/DS
1024MB/CORSAIR/CM3X1024-1333C9DHX/DS(Double-sided)
Visit the ASUS website for the latest DDR3-1600/1333/1067/800MHz QVL.


---

### Post by WB0HYQ on 2021-03-27
> **vmpx said:**
> In User Guide of my motherboard:

@vmpx: Your motherboard is nothing like mine. I can support two modules only, each of 8GB. They have worked just fine for over 4 years. Due to my 50+ years in computers, I know how to check, and retain, any good modules. Both the original and the replacements I bought are good modules. The fault lies in either the motherboard or the CPU's MMU.

@bcschmerker: A very good idea. I don't remember what CPU was put into the slot, but the MOBO specifications are here: [https://www.msi.com/Motherboard/760GM-P23-FX/Specification](https://www.msi.com/Motherboard/760GM-P23-FX/Specification) This was a replacement CPU for a slower one. It isn't overclocked. Just run normally. I have the older, slower CPU, so I might drop it in temporarily to see if it fixes the running of memtest. if it passes, then the CPU is faulty and I'll replace it. Thanks for the clue.

Bill

---

### Post by vmpx on 2021-03-27
I have:
> 
CPU: LGA775 socket for Intel Core 2 Quad - Q9550
Chipset: Intel X48 / ICH9R with Intel Fast Memory Access Technology


---

### Post by WB0HYQ on 2021-04-28
Finally! The new CPU I ordered arrived after a month of being strapped on the back of a turtle coming from China. Using both the new and old RAM modules, I get exactly the same MEMTEST results. Looks like the MOBO is fried. Don't know if a MOBO-transplant is even worth it, given how old the box is--despite the upgrades in power supply (250W to 475W), RAM, video card, internal HDs, and even a new DVD unit.

Bill

---

### Post by WB0HYQ on 2021-05-27
I am back to square one. I have three laptops (of varying vintage) and a second desktop (slightly newer than my primary desktop) and all are running 20.04. On a whim, I ran the Boot Menu MEMTEST. Each and every one of them failed at exactly the same spot (66%) in the default memory test.

All of them can't be bad. It is my opinion that the MEMTEST is flawed and cannot be relied upon for diagnosing memory problems.

Bill

---

