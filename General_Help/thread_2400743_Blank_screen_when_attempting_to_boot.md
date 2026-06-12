---
title: "Blank screen when attempting to boot"
date: 2018-09-09
forum: General Help
---

### Post by nonbeing2 on 2018-09-09
[s]To begin with, here's my basic hardware info:
CPU: i5-6500 @ 3.20 GHz
GPU: AMD RX 480 (Polaris)
Motherboard: MSI 7972
1080p resolution
I also have a windows partition on the drive.

Less than a month ago, I made a clean install of 18.04 on my desktop. I've been using it near-daily without issue since then. Last Thursday night I was using it and did nothing extremely unusual. I browsed some (popular, well known) torrent sites while using ublock origin, but ultimately didn't download anything, then later that night played a steam game. I don't recall if I shut down the computer between these two activities. I didn't install any new software, run strange programs, or make changes to system configurations. It's possible I may have done a routine apt upgrade, though I don't remember specifically. When I next turned on the PC Friday night, I saw the bios screen and grub as usual, but after selecting Ubuntu in grub, the screen went black and mostly unresponsive (rather than showing the loading screen and then the login interface). The monitor was still getting a signal from the pc and was displaying an image, but said image was a solid black screen. I was not able to drop to any of the text-only teletypes. The only things I can do that get a response from the system are turning num/caps lock on and off (as indicated by the keyboard light) and REISUB. So I rebooted and experimented a bit, and have so far found the following:

-Windows 10 boots fine from grub and has no problems.
-I found nothing unusual in the BIOS menu settings.
-Currently, I have the most recent kernel patch installed (ending in 33), but the previous one (ending in 32) is also still installed. The bug persists with no difference regardless of which version I boot into.
-I **am** able to boot into recovery mode, see the interface, and run the options from the menu. While in recovery mode, I ran fsck and update-grub. Furthermore, I am able to "resume". This brings me to the normal loading screen, albeit in 480p (presumably, this is one of the expected graphical issues the os warns you about when you resume). I was able to log in and perform and apt upgrade. I checked system details and it listed my gpu incorrectly (again, probably because of recovery mode issues).
-The bug still persists after doing all this.

Somebody suggested to me that this could be a driver issue, but I think that is unlikely because nothing about my driver changed in-between Thursday night and Friday night. Since I have a newer AMD card, my driver is the free-software version of AMDGPU, which is included in the Linux kernel (I do not use AMDGPU-Pro). When I used OS last Thursday, I was certainly running one of the two kernels mentioned above. On windows, the gpu software and System Information display correct information about the card and nothing appears to be out of the ordinary. It is also unlikely that the PC was damaged physically in between uses, and there are no obvious signs of such.

If there are any logs I should provide, let me know where they are stored and I will try to post them here.

Edit: I just tried booting into an 18.04 live USB&#8212;the same one I used to install 18.04 on my pc a month ago, created a few months before that&#8212;and had exactly the same bug. Went through grub, got a blank screen, had to REISUB out. Unfortunately, this suggests that I will not be able to "solve" the problem with a clean reinstall. It also makes this bug even more mysterious, and seemingly points to a hardware or firmware problem. I don't see how anything about the (gpu) firmware could have changed between thursday and friday though: the computer wasn't turned on. And hardware damage seems unlikely since windows is working fine. I'll take a look inside the machine and see if anything is out of place.[/s]

Edit 2: lmao... remember when I said it was a hardware problem? technically correct. I reached back and pushed the hdmi cord further in and sure enough when I stood back up there was the login screen, so problem solved. at least nobody wasted their time replying to this yet. still have no idea why one os worked and the other didn't though.

TL;DR Did you try unplugging it and plugging it back in again?

---

