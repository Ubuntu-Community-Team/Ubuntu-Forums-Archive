---
title: "Graphics Drivers Not Functioning?"
date: 2008-06-18
forum: General Help
---

### Post by InRainbows on 2008-06-18
[IMG]http://i31.tinypic.com/16a776c.jpg[/IMG]
**I have a Fujitsu Lifebook P1120**
SPECS:
[LIST]
[*]800MHz Transmeta Crusoe Processor (comparable to a slightly lower-clocked Pentium 3)
[*]256MB of RAM (unexpandable)
[*]30GB Hard Drive
[*]ATi Mobility Radeon LY
[*]8.9" Touchscreen
[*]Integrated Atheros 802.11g Wi-Fi
[*]NO OPTICAL or FLOPPY DRIVE
[*]NO BOOTABLE USB OR CD-ROM (hard drive had to be removed and Linux was installed using another computer)
[*]Xubuntu 8.04
[/LIST]

It originally had Windows XP SP2 on it, and it actually ran rather well. Firefox could play Youtube videos at a good 15-20fps, and loadup times were fast.

Now I install Xubuntu 8.04, and the machine is now slow as molasses. Youtube videos are complete slideshows, and loadup times can take onwards of 6 minutes!

[IMG]http://i26.tinypic.com/5x8ps0.jpg[/IMG]

I have a feeling its the video drivers which are causing this problem, because anything I do graphically shoots up the CPU Usage and all actions have a delay of up to a minute. I simply move the mouse and my CPU Usage goes from 74% (idle) to 99%!!

It HAS to be the graphics! I mean, why would XP SP2 run like a Ferrari compared to Xubuntu Linux!?!

I read the thread about the Mobility LY driver, and I just don't know how to do it. I've never used Linux before, so I know nothing about getting root and terminal and such. I have no choice, however, because this laptop has no optical drive or bootable-anything, and you cannot install XP on another computer and just move the hard drive to the laptop (whereas in Linux, you can).

What do I do?
#1 - It has to be the graphics drivers right?
#2 - What do I do? I can't even access any info about my drivers in the "Applications" menu, so I can't even tell whats going on!

---

### Post by InRainbows on 2008-06-19
One of the reasons why Linux will never go mainstream or even become more popular among the power-user and IT communities is because this kind of thing happens, and when someone goes for help, you guys are all freaking USELESS. Have fun wallowing around in your source code, coffee-addicts!

---

### Post by rdawg on 2008-08-31
I have the Fujitsu P1110. Exact same thing except it does not have the wireless built-in already. I use a Cardbus wireless adapter.

I was just wondering if you ever figured out or anyone, on how to solve this problem. It is ridiculous, the windows XP that was installed on this machine was WAYYYYYYY Faster. I figured that Xubuntu would be the best OS on here but heck no. Any help in leading to a fix would be very much appreciated.

---

### Post by Tom--d on 2008-08-31
The reason you are not getting an answer is probably people don't know the answer to it.

Try these things:
Go to System > Admin > Hardware Drivers > Anything listed? Like ATI? if so, enable it.

Next, With youtube etc(flash things), use Flash player 10 (not 9) because flash player 10 has way more better support for Linux than 9.

Also, do not use System Monitor because it has a bug and causes the cou to do more work.

Post a screenshot of top.
Go in terminal and type in top and press enter.

---

### Post by boyanov on 2008-09-09
There's another article that may help you: [http://ubuntuforums.org/showthread.php?t=68489]("http://ubuntuforums.org/showthread.php?t=68489")
Look at the suggestions by **warp99**.
Good luck :guitar:

---

### Post by rdawg on 2008-09-26
Thanks, I will see what I can figure out by using this. :)

---

