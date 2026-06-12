---
title: "Nvidia drivers have 'broken' my PC."
date: 2018-04-09
forum: General Help
---

### Post by rayburn2 on 2018-04-09
(ubuntu 17.04)
When a game that normally runs fine crashed, I decided it was time to try to update my Nvidia drivers for my GTX 660. I just do this by selecting a non-proprietary driver in the Additional Drivers GUI then selecting the recommended proprietary driver again. However this time whenever I tried to apply changes the selection would revert back to the nouveau driver. Stupidly I rebooted to try and fix the problem. 
Ever since then I've had many problems. To start with I couldn't log in and was stuck in a login loop. In the Ctrl+Alt+F1 VT I tried to go back to the old driver but it would not select. So eventually I had to remove the nvidia drivers.
I can now log into my account but the PC crashes fully after between 1-10 minutes or whenever I try to access any program remotely taxing (often including the driver GUI). My PC is now unusable as it crashes too often and my only thought is that it must be the drivers as it was fine before. Checking through the terminal the Nvidia drivers are no longer on my PC and have not reinstalled after many attempts.
I don't really want to have to do a fresh install of Ubuntu as I have lots of files that I have not yet backed up and a project that I am halfway through. I have tried to back these up onto a flash drive, but it causes the computer to crash.
What I really want is a quick fix somewhat soon. I have tried quite a few times to no avail to correct the drivers. I was wondering if anyone has experienced anything similar or knows of any ways to fix it. Thanks in advance and sorry for the long article.

I have been using nvidia proprietary driver 384 and it was working just fine.

Edit: I have been able to get onto the GUI drivers settings but they just revert. It still crashes, I was just lucky.

Edit : when listing my drivers on VT the only driver that appears is for my CPU. Nothing at all for the GPU. Nouveau appears to be disabled.

---

### Post by Yellow Pasque on 2018-04-09
If you boot with nomodeset, does that stop the crashing?

> (ubuntu 17.04)

is EOL and no longer supported. You should be looking at doing a fresh install of 18.04 when it comes out in a couple weeks (or even use the beta iso if you can't wait).

---

### Post by rayburn2 on 2018-04-09
Can't actually find out how to launch with nomodeset. I've tried and failed to get into the grub2 launch menu. I'm sticking kinda new to Linux.

---

### Post by Yellow Pasque on 2018-04-09
You hold shift after BIOS/EFI screen and then add 'nomodeset' where it says 'quiet splash' or something like that

---

### Post by rayburn2 on 2018-04-10
Tried that. Still crashed but gave me enough time to save my important files to a flash drive. I managed to check the additional drivers and the GPU drivers are now non-existent, they do not show up and there are no settings to change them. This may be the cause of the problem - I just can't seem the be able to reinstall them. Thanks for the suggestion, at least I can do a fresh install if I need to.

---

### Post by missmoondog on 2018-04-10
no help at all here but welcome to the nvidia screwed my system club!! 

i don't know how many times nvidia screwed my systems up to the point of reinstalling in the past, or how many times i've read of those instances around the net. this was a long time ago for me as i quit even trying to use linux because of that for years.

still very skeptical about installing nvidia drivers to this day, but haven't had any issues with the last 2 versions of lubuntu lts releases.

can't wait for lubuntu 18.04 lts but not doing a beta os!! :)

---

