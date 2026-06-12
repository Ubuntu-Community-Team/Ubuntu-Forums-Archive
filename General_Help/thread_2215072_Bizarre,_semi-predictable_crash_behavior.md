---
title: "Bizarre, semi-predictable crash behavior"
date: 2014-04-04
forum: General Help
---

### Post by john_ladasky on 2014-04-04
Hi folks,

I'm not sure whether I'm developing a hardware problem, or whether this is a software issue.

_My configuration:_ Gigabyte MA-GM78-US2H motherboard, vintage 2009. Older, but not ancient.  AMD 1090T 6-core CPU. Ubuntu 13.10, 64-bit.  NVidia 760 GPU, with 319.xx series GPU drivers.

_My symptoms:_ They began about a month ago.  When I first boot up the system in the morning, it freezes solid about 3 minutes after logging in.  The mouse pointer simply stops in mid-gesture.  The keyboard locks up completely.  I have to reach down to the console and force a hard reset. (I suspect that these daily hard resets were the cause of my recent hard disk superblock failure.  I had to reinstall Ubuntu.  Fortunately, I keep good backups.)
[U]
The mystery:[/U] Upon reboot, the system functions perfectly.  For the rest of the day.

Any suggestions how I might track down this problem?  Thanks!

---

### Post by Futant on 2014-04-04
Can you use [REISUB]("http://blog.kember.net/articles/reisub-the-gentle-linux-restart/")? At least that would be better than a hard reset. No idea about the problem though :(

EDIT: Sorry just realised you said your keyboard locks up. It's been a long day.

---

### Post by tgalati4 on 2014-04-04
I would check the voltages of the power supply (in BIOS or with a meter).  I would also inspect the motherboard for bulging or leaking capacitors.  The fact that a quick reboot brings it back is consistent with a power issue.  It's also possible that your nVidia card is acting up.  After 3 minutes, it heats up and causes a fault.  The reboot allows the card to function while it is already warmed up.  Have you cleaned out the dust with compressed air?

Log in via ssh from another computer.  If it locks up again, go to the other computer and see if the ssh session is still functioning.  If so, then you can look through the log files for clues.

---

### Post by john_ladasky on 2014-04-04
> **tgalati4 said:**
> I would check the voltages of the power supply (in BIOS or with a meter).  I would also inspect the motherboard for bulging or leaking capacitors.  The fact that a quick reboot brings it back is consistent with a power issue.  It's also possible that your nVidia card is acting up.  After 3 minutes, it heats up and causes a fault.  The reboot allows the card to function while it is already warmed up.  Have you cleaned out the dust with compressed air?

Log in via ssh from another computer.  If it locks up again, go to the other computer and see if the ssh session is still functioning.  If so, then you can look through the log files for clues.

Thanks for your reply, tgalati4.   I run some computationally-intensive jobs, so I am aware of potential heat issues. I do monitor my system temperatures, both the CPU and the GPU, with psensor.  On the first boot, the system is running quite cool, as you would expect -- high 20's for the CPU, high 30's for the GPU.  But the temperatures don't get bad even when I am running the system flat-out overnight: CPU temperatures reach the low 50's, and GPU temperatures reach the low 60's.  The interior of the case was recently cleaned with compressed air.  That being said, I will repeat my observation that temperatures are well within acceptable limits.  If there is a thermal issue, it would seem to be a function of the system being... too cold when I first turn it on?

I will follow up on your suggestions to check for incorrect power supply voltages, and for leaking capacitors.

---

### Post by tgalati4 on 2014-04-05
The CPU's can take the heat, but the motherboard degrades over time with heat.  Delamination of the ball-grid-array soldering or corrosion/cracks of the copper traces within the layers of the motherboard can cause lockups.  Motherboards tend to wear out with constant high loads--funny, but the CPU's tend to outlast the motherboards.  On workplace number-crunching machines that exhibited similar behavior, I had luck with declocking the machine.  Slow it down slightly.

Try moving the RAM around.  Run 30 complete cycles of memtest.  If you get errors, then try declocking or add wait states to the RAM.

---

### Post by dragonfly41 on 2014-04-05
> I'm not sure whether I'm developing a hardware problem, or whether this is a software issue.

My approach would be to try to pin it down to hardware or software first.

e.g. .. does Live CD run without these crashes?

---

### Post by john_ladasky on 2014-04-05
Dragonfly, that's a good suggestion.  I'll try the Live CD a few times -- when I do not need convenient access to all the applications and data I have installed on my hard disks.

---

### Post by coldraven on 2014-04-06
> **tgalati4 said:**
> The CPU's can take the heat, but the motherboard degrades over time with heat.  Delamination of the ball-grid-array soldering or corrosion/cracks of the copper traces within the layers of the motherboard can cause lockups.  Motherboards tend to wear out with constant high loads--funny, but the CPU's tend to outlast the motherboards.  On workplace number-crunching machines that exhibited similar behavior, I had luck with declocking the machine.  Slow it down slightly.

Try moving the RAM around.  Run 30 complete cycles of memtest.  If you get errors, then try declocking or add wait states to the RAM.

FWIW The Wikipedia article on the disadvantages of ball-grid-array soldering CPUs to motherboards. This obviously will not apply if your CPU is in a socket.
[http://en.wikipedia.org/wiki/Ball_grid_array#Disadvantages](http://en.wikipedia.org/wiki/Ball_grid_array#Disadvantages)

---

### Post by tgalati4 on 2014-04-06
Most CPU's are in sockets.  But all of the support chips are surface-mounted.  If those delaminate, then your motherboard is trash.

---

### Post by john_ladasky on 2014-04-09
Hello again,

Here's a partial followup.  I have had the crash occur a few more times.  I happened to look down at my keyboard for the first time when the crash occurred, and what I saw was that the caps lock and scroll lock lights were flashing.  I saw it a second time as well.  Maybe it has been happening every time the system has crashed, I just didn't notice.

An Internet search suggests that my system is experiencing a Linux "kernel panic."  I need to better understand exactly what a kernel panic is, and whether my system might be logging any information about it when it happens.

As always, if my system crashes, it crashes within the first few minutes of operation, and it works fine after a hard reset.  Mysterious.

---

### Post by dragonfly41 on 2014-04-09
What was the outcome of running Live CD a few times to provide a reference point (re: hw vs sw)?

---

### Post by john_ladasky on 2014-04-11
> **dragonfly41 said:**
> What was the outcome of running Live CD a few times to provide a reference point (re: hw vs sw)?

I have tried the Live CD twice so far.  The first time, I ran for over a half hour without trouble, and then I rebooted.  However, I'm not sure that this first test was a good control, as I had shut down the computer mid-day, and I tried the Live CD in the evening.  The system was turned off for a few hours between runs, but the conditions were not exactly the same.

This morning, I tried booting from the Live CD while the system was still "cold."  I DID get a lock-up.  The mouse pointer froze.  The keyboard was unresponsive.  However, the caps lock and scroll lock lights were not blinking.

I have conducted a cursory examination of the system in its case.  I don't see anything egregious, no leaking capacitors on the motherboard or anything like that.  However, I think that I would have to disassemble the system completely in order to get a good look.

---

### Post by dragonfly41 on 2014-04-11
It is difficult to pin down crashes in such circumstances.

Some first troubleshooting questions I can think of ... no guarantees that any of these might work .. 

Does the system freeze if you just login and leave it running without any apps launched?

Can you try creating a new user account and running in that account. Others in forum have written that this solves freezes (although if this new account is stable you have to move over your old user profile app by app into your new user account which might be a long process).

Have you tried unplugging your mouse and either using a replacement or none at all?

Can you install system monitor (through Software Centre) and observe resource usage?   Applications > System Tools > System Monitor.

Does the freeze occur when you are running browser such as firefox?

Do you have many tabs active in your browser? Perhaps YouTube embedded flash or other video streaming or games which are running in background?

Have you tried running browser with add-ons disabled? Firefox > Help > Troubleshooting.

Have you tried the suggestion in post #5 to change around memory cards (or if you have two try running with one at a time to see if there is a failure)?

Have you tried running memtest in Grub menu?

Have you tried System Testing.   Applications > System Tools > Administration > System Testing?

Have you tried running bleachbit to clean up cache?

[COLOR=maroon][Later edit]

If you google "ubuntu 13.10 cursor freezing" you'll find a number of possible clues .. e.g. one here ..

[http://news.softpedia.com/news/Ubuntu-13-10-Hit-by-Annoying-Unity-Freezing-Bug-397907.shtml](http://news.softpedia.com/news/Ubuntu-13-10-Hit-by-Annoying-Unity-Freezing-Bug-397907.shtml)
which refers to memory leak.

Perhaps try switching to Gnome Classic mode at login?
[/COLOR]

---

