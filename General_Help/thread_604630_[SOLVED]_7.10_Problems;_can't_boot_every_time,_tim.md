---
title: "[SOLVED] 7.10 Problems; can't boot every time, time runs too fast, keyboard is crazy"
date: 2007-11-06
forum: General Help
---

### Post by Nehvrook on 2007-11-06
[Solved]

Apparently all of these problems were caused by the clock moving too fast. It was forcing the OS to run that fast with it (Literally, in quake I'd tap the mouse button and an entire clip of ammo would be gone XD) I added "clock=tsc" to the kernel section in grub and it fixed all of the problems. weird.



Summary: 

I can't get the proper kernel to boot consistently, sometimes it will boot, sometimes it won't. When it does boot time runs way to fast and affects the whole system, mouse clicks register hundreds for every physical one and the same with keypresses. Anyone got any idea;s

Detailed version:

I recently upgraded from 7.04 to 7.10 and when I went to boot into 7.10 all I got was a black screen. I didn't have much time so I left Linux like that for a while and used windows.

Today I've gone back and tried to see what the problem was. In Grub I have four options. Two for 7.10 the latest Kernel (something ending in .22.14 I think) and two for an older Kernel (Which I think ends in .20.16)

Loading the one I should be using (.22.14 at the top of the list) I get nothing but a black screen. There's no Ubuntu loading splash screen and I've left it for over ten minutes and never reached the login screen. So I tried running it in recovery mode and I got a load of error text followed by "Failure Registering capabilities with primary security module" and had to physically reset the PC.

So I booted up again and loaded the old kernel, and it took me through a load of text stuff and let me into Ubuntu in "Low graphics mode" From in there I was able to connect to the internet and I updated using the auto-updater tool, though I wasn't able to set resolutions and things like that. 

I restarted the PC and this time it let me boot into Gutsy properly (With the right kernel), apart from it flickered while the loading screen was on. But when I went to type my user name every key I pressed printed a LOT of characters. I managed to get logged in by highlighting and deleting and I managed to get the keyboard to behave normally by turning off repeat key presses in the keyboard settings.

However the screen saver kept coming on every few seconds even though it was set to 20 minutes, and the clock was running insanely fast (After being logged on for about five minutes it had counted nearly 12 hours)

I thought I'd restart to see if it made any difference, but now I can't boot back into Ubuntu again.


I'm thinking it might be better all round to just use the Live CD to save my files, and format a fresh copy of Gutsy over the top.

If anyone has any idea's on how to fix this please help, and thank you for taking the time to read what is probably too long a post.

---

