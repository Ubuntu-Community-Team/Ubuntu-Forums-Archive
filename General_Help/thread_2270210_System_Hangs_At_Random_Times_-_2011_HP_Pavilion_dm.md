---
title: "System Hangs At Random Times - 2011 HP Pavilion dm1-4027ea"
date: 2015-03-21
forum: General Help
---

### Post by Anigai on 2015-03-21
Hi guys, I'm a long time Windows user(15 years) and short (4 months) Linux and general Ubuntu user. 

I'm having an issue with my system hanging up on me in all operating systems I use and I think it's due to general wear and tear on my netbook from 2011 which has seen daily use both for standard and heavy tasks. I even recently replaced the HDD as the old one could not write reliably anymore but everything was saved thankfully but the problem has persisted since the replacement last month with a fresh install of Windows 7 and a few other distros eventually bringing me back into Ubuntu where I started.
At the same time I replaced the thermal paste on the CPU for the 1st time though I should have done that more often.

I first noticed the issues occuring in December 2014.

_Symptoms_
-All Linux distros including Ubuntu, Mint, LXLE & Debian and their other versions (e.g. xubuntu) freeze at seemingly random times with use of REISUB being 100% ineffective.
-Windows 7 ironically slightly more stable although extremely slow with explorer.exe even after reinstalling the OS.
-Firefox has issues which have caused it to freeze in Windows requiring Windows Task Manager and is also the most common application that causes Ubuntu to hang that I use.
-Very underpowered CPU has been at 100% use for long periods of time while waiting for operations to finish regularly.

_System Infomation_ - 2011 HP Pavilion dm1-4027ea
CPU/APU - AMD E-450 APU @ 1.65GHz Dual Core with AMD Radeon™ HD 6320 Graphics
RAM - 4GB of DDR-3 @ 1333MHz with 3.49GB usable.
New HDD - Toshiba MK3276GSX 320GB SATA I.
Operating System(s) - Windows 7 and Ubuntu dual booting.

_Notable System Changes_
- New HDD February 2015.
- Switched to 100% use of ethernet cable over 100% use of wi-fi as router is right beside me all the time in March 2015.

_Attempted Fixes_
-Installing numourous linux distros.
-Reinstalling Windows 7.
-REISUB is not recognized despite slow methodical key strokes in all Linux distros when problem occurs.

[U]Tests Ran With Results And Dates
[/U]-Memtest86+ v4.20 on 19\03\15=  Uncompleted test though 6 errors were listed leading to repeat test following day.
-Memtest86+ v4.20 on 20\03\15=  1 Pass from Ubuntu 14.04.2 Live USB with no errors listed. Test took 1 hour to finish.
-Prime95 20\03\15 = No issues after 10 minutes.

I've tried to list everything in a way that I'd like someone to if I were trying to provide them with support personally but please do ask if you think I've left anything out that might help.

I'd also just like to preemptively thank anybody who's willing to give me a hand with this as I'm really grateful for it.

---

### Post by Anigai on 2015-03-22
24 hour bump.

I can at least find solace in the fact that it's not getting any worse so far. The only downside is I'm limited to using windows since it's just applications that hang versus the entire thing in Ubuntu but it would be nice to be able to use it.

---

### Post by dino99 on 2015-03-22
which ubuntu is used ?
is swap partition used ? (compare output of 'sudo blkid' and 'cat /etc/fstab') the swap uuid have to be identical.
You might also check for possible errors logged into ~/.Xorg.0.log (ctrl+h to unhide it) and into /var/log/

---

### Post by Anigai on 2015-03-22
After running those 2 commands in a terminal I can confirm that the uuid's match up no problem.

I'm assuming that Xorg file should exist in my home directory as a hidden file which it does not. It also doesn't not exisst in /root either, is that where it should be?
Using nano in a terminal (I'm a long way off mastering vi) I looked into some files in /var/log/ and since most issues in the files are dated and I can only pin down my last system hang up to sometime last night it's going to be hard to find. My only option seems to be that during the next hang I'll have to record the date and time that it happens and work from from there.

Thanks for the help.

---

### Post by Anigai on 2015-03-23
I just had a hang up at 19.24pm while trying to watch an episoe of he-man from the 80's. I only just booted up and it wasn't on for even 10 minutes and I didn't make it past the opening either.

I'm looking at Xorg.0.log in /var/log at the moment and I'm not 100% sure how to read it but it looks like there are no issues.

The issue seems to only happen during any moderate graphical rendering, it's leading me to believe that my APU is failing, at least the GPU side of it anyway. I guess the old Rasberry Pi project is back on the books since I can't afford a new computer at the moment lol

---

