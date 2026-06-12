---
title: "Splash Screen Unresponsiveness"
date: 2015-09-19
forum: General Help
---

### Post by Brandon_B on 2015-09-19
Hi, I've just recently installed Ubuntu 14.04 on my system. The installation process gave me no troubles whatsoever. I installed on to a secondary SSD while leaving my Windows 7 installation on my original SSD. Anyways, after installing via. a live CD I got onto my new Ubuntu installation, downloaded a few programs (Google Chrome, Steam) tested everything to make sure it was all working right (I am new to Ubuntu and wanted to be thorough). I had no problems at all. Finally, I shut my PC down for the night.

Today, on booting my PC up I missed the opportunity to hit "F12" at the BIOS screen and so I booted straight into my Windows 7, as per default. This being the first time I'd tried to boot Windows since installing Ubuntu I figured I'd check things out and make sure it was all still running fine (and it was). Now, I rebooted the system, hit "F12" at the BIOS screen, selected the SSD containing Ubuntu and was sent to GRUB (which I hadn't seen up until now - previously I'd either gone straight into Ubuntu OR had missed it due to the loss of signal my screen experienced during the boot process). In any case, I selected the default Ubuntu option in GRUB and hit my first blank screen. At first I waited, hoping it was just a slow loading process - it was not.

I began Googling for some solutions others had found for this problem - I ran the recovery mode from GRUB and attempted several things here - running dpkg seemed to make a lot of changes, the text scrolled quite quickly for me to see though. This did not solve the problem. Trying failsafeX brought me into a CLI where I was prompted to log in, I also find an error of some sort here: "BrandonComp login: initctl: Event failed" (BrandonComp being the name of my machine).

I attempted using a variety of parameters by editing the default Ubuntu command through GRUB. I tried altering this line: "(...) quiet splash $vt_handoff" into the following:

"quiet splash nomodeset $vt_handoff" - this, interestingly enough, changes the splash screen that I am freezing on. Instead of a blank screen I am shown the Ubuntu logo with dots beneath it (the typical loading screen I would see here) however it is also frozen and I am unable to progress from here.

I also tried:

"quiet splash nomodeset nolapic $vt_handoff" and "quiet splash acpi=off nolapic nomodeset" which were suggested on askubuntu.com under the question "ubuntu 14.014 black screen when installing", though the problem was different I thought it may have applied, but neither of these seemed to work either.

I'm really a rookie when it comes to Linux at all - nevermind troubleshooting it, if anyone could help me in determining what I might try next I would really appreciate it, I'd hate to continue being stuck with Windows. Everything I've mentioned here is reproducible so I'm certain the problem is tangible enough to be diagnosed, I just don't know how to approach it.

---

