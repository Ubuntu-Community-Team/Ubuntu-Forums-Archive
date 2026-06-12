---
title: "Black Screen on Startup"
date: 2015-08-21
forum: General Help
---

### Post by james162 on 2015-08-21
Hi all, I am a new Ubuntu user with 3 days of Linux experience under his belt! I immediately got attached to the new environment and have been loving every moment since. Given this, I am willing to do all necessary troubleshooting to get it back up and running again despite having little in the way of computer knowledge.

_First, my comp's specs:_ It's a brand-new Gigabyte Brix BXi5-5200U. It has a 256gb SSD and 16gb of ram. The GPU is the integrated Intel HD5500 chip.

_Ubuntu ver.:_ 14.04

_So here's the issue:_ I have a blank screen upon booting my computer. But as I went with full disk encryption, I at least get the prompt to input my encryption password first. After successfully doing this, I get a blank screen with the mouse pointer in the middle and nothing else.

_How this happened:_ I wanted to see how my computer performed, so I installed Steam for Linux on it yesterday. It played a small game flawlessly. So far so good. This afternoon, I decided to stress it a bit further and installed Portal 2. I barely got 5 minutes into it that the screen froze, started tearing and would flicker between the black screen and the graphical glitching. I closed the comp and since then, it has shown the blank screen on startup.

Every so often, I had been monitoring ram usage and cpu temp. Idle, it showed low numbers. As of yesterday, I saw a process called "compiz" show up which took up a large chunk of ram. Even before opening Steam, it was using up a whooping 13gb of my memory. Even so, I went ahead with the Steam test. Before crashing, I saw the cpu temp reach 75c. Could Compiz and the memory/cpu load have anything to do with this problem?

If anyone can help, it would be greatly appreciated! Thanks!

---

### Post by james162 on 2015-08-21
Ok, so after *a lot* of tinkering and trial-and-error, the solution was simple: reboot from recovery mode. This must have reset the gpu drivers or something and now it's running smooth again. Compiz is back to normal using 1gb of ram or less so far.

Sadly, I think this issue is going to crop up again, so until I manage to identify the root cause, it may persist. I'm glad there's a simple workaround in the meantime, however.

---

### Post by james162 on 2015-08-22
Turns out this issue is due to a corrupted driver. Other users have had this problem. The i915 driver bugs out for one reason or another and then you have a black screen. The user resolves this issue and is left with something else -- Linux will recognize the HD5500 integrated gpu as an inferior chip. Anything requiring the use of the gpu will have vastly reduced performance.

Unfortunately, in the process of trying to restore this driver to its proper state, I made a mistake. It was proposed to open the Xdiagnose program and check the box that says "disable bootloader graphics". I did so, and now have no clue how to revert this state. If anyone knows, it'd be greatly appreciated as I currently only have access to Terminal upon system startup.

---

### Post by james162 on 2015-08-23
I'm tearing my hair out here - does no one know how to operate Xdiagnose from Terminal?

Any help is appreciated.

---

### Post by HermanAB on 2015-08-23
BTW, one way around the black screen problems is to install sshd.  Then, when your machine black screens, you can log in from another machine and fix it.

---

### Post by james162 on 2015-08-23
That is definitely an option I'll be looking into. Thanks for that.

I finally got back to desktop as well. The solution was... pretty simple, actually. I just didn't know about it. All you do is go to Terminal and input "startx". Then you open Xdiagnose from Terminal once back to desktop and uncheck the box.

I remain left with no graphics save for desktop icons and the default Ubuntu wallpaper, however. Going to have to find a way around that.

EDIT: to add to the above, I can open any app through Terminal. I just don't see the GUI.

---

### Post by james162 on 2015-08-26
So I am now attempting to reinstall Ubuntu, but it will not boot from my USB for whatever reason. All you have to do is insert it and it will boot from that, correct? If so, it simply is not working.

As it stands, I must access my computer every time through the "startx" command, and it still behaves as though bootloader graphics are turned off. What a load of crap that advice was!

Anyway, my gpu is currently recognized as a "Gallium 0.4", which it isn't. It's an HD5500. Maybe correcting this would restore things?

---

### Post by sandyd on 2015-08-26
> **james162 said:**
> So I am now attempting to reinstall Ubuntu, but it will not boot from my USB for whatever reason. All you have to do is insert it and it will boot from that, correct? If so, it simply is not working.

As it stands, I must access my computer every time through the "startx" command, and it still behaves as though bootloader graphics are turned off. What a load of crap that advice was!

Anyway, my gpu is currently recognized as a "Gallium 0.4", which it isn't. It's an HD5500. Maybe correcting this would restore things?

Gallium is just the driver architecture for the open source intel driver.

Try using the latest Intel Graphics Stack Installer from [here]("https://01.org/linuxgraphics/downloads")

---

### Post by james162 on 2015-08-26
I don't know why it's displaying as that, though. It was recognizing it as an HD 5500 before and changed to the Gallium name following my black screen issue. Graphics were also noticeably poorer subsequently.

Anyway, that's a non-issue as I'll be re-installing Ubuntu the moment I can figure out how...

---

### Post by Geoffrey_Arndt on 2015-08-27
If your PC has optical drives, you can use DVD instead of flash-stick to reinstall.   Also, to boot from USB flash drive, on many systems, you have to change the boot sequence in the bios/uefi first and save the change.   I have a laptop without an optical disk., and 99% of the time I don't need one, but when I do, I just plug in a USB external dvd/cd device.

---

