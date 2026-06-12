---
title: "[SOLVED] Reset BIOS causing freezing issues"
date: 2007-12-19
forum: General Help
---

### Post by Junction on 2007-12-19
This past summer, I installed Dapper onto a second hard drive on my computer .  It was my first foray into using a linux OS, and it seemed to run great at the time, giving me no problems at all.  

But then a little over a month after I installed it, my neighborhood had a short power outage while I was using the computer.  When it came back on and I tried to boot up, I got an error from my BIOS, saying that it couldn't restart, and asking if I wanted to reset the BIOS.

I should probably point out here that the computer was given to me as a gift a couple of years ago, so its BIOS settings at the time had not been set by me.

Ever since that day, Ubuntu tends to completely lock up randomly, where the only thing it seems to respond to is the Number Lock key and Sys Rq commands.  The freezes seem to be completely random to me, and Ctrl+Alt+Backspace and the like have no response.  I've fiddled a bit with my BIOS, used different video drivers (it's an ATI card, so I thought that could be an issue), fiddled with my Xorg.conf file, formatted the drive and reinstalled Ubuntu, but the problem remains.  It happens when using a Live CD as well.  I ran MemTest for 6 hours, and it didn't seem to spot anything wrong.

I've got Windows XP on the other drive, and it has never acted up throughout all this, so I'm still able to use the computer, but I'd really like to be able to get Ubuntu back running reliably again.  I realize that, since it was a change in the BIOS that seems to be the culprit, it is probably something in there that I've got to change, but I have no idea how to figure out what it is.

---

### Post by gobbles414 on 2007-12-19
Hi Junction,

Sometimes, one must disable *legacy USB* support in a computer's BIOS in order for a Linux installation to function correctly. And if you do not have any critical data on the hard drive that you have been using for Ubuntu, you might consider upgrading to Ubuntu 7.10. Let me know if either of these ideas solves your problem.

---

### Post by Junction on 2007-12-19
Thank you very much for the response!  I've already updated to 7.10; my apologises for not mentioning that in my post.  I've just now turned off legacy USB support, and will try and see tomorrow if it'll still act up or not.

---

### Post by gobbles414 on 2007-12-20
Hi Junction,

Did you do a "clean install" when you updated to Ubuntu 7.10?

---

### Post by Junction on 2007-12-20
I can't say that I did.  My last clean install was 7.04, and then I just upgraded to 7.10.

As a status update, I've had ubuntu running for about 9 hours since I've turned off Legacy USB support in the BIOS, and so far, no lock ups.  There have been a few times in the past where it would be up longer than this before a lock up, but most of the time it would have frozen up on me by now.  So things are looking very good so far.

---

### Post by Junction on 2007-12-20
Hmm, went to the store just now, and when I got back my computer had frozen like usual.  Drat.

---

### Post by gobbles414 on 2007-12-21
Junction,

To be honest, I also did an upgrade from 7.04 to 7.10 instead of doing a clean install. Shhh... :-$ Anyway, could you **please provide your system specs.** You might be experiencing a driver issue of some sort. Or your system may have met the system requirements for 7.04, but not 7.10. Here's a list of information that you'll need to post:

* RAM -- how much and what speed (e.g. 2x1GB @ 533MHz)
* Processor -- model and MHz (e.g. Intel Core 2 Duo @ 2.0GHz)
* Hard Drive -- size and speed (e.g. 160GB @ 5400RPM)
* Graphics -- model, size, integrated or dedicated (e.g. NVIDIA GeForce Go 7700 @ 512MB, dedicated)
* Software that you have installed since upgrading to 7.10 (e.g. Automatix2)
* Anything else that you believe to be relevant (e.g. my power settings are set to never go to sleep or turn off the hard drive)

EDIT: I forgot perhaps the most important item of all! Are you running 32-bit or 64-bit Gusty?

---

### Post by Junction on 2007-12-22
Sorry for not responding quicker.
Um, I wasn't the one who put this computer together, so I'm not very familiar with all the specs, but here's what I do know, to the best of my knowledge.

[LIST]
[*] Running 32-bit Gutsy
[*] RAM -- 1 gig total (Two 512MB modules, no idea about speed)
[*] Processor -- Intel Pentium 4 @ 2.53 GHz
[*] Hard Drive -- 40 GB, speed uncertain, is the drive that ubuntu is on.  My other drive is 80 GB, speed also uncertain.
[*] Graphics -- ATI Radeon 9700 Pro @ 128 MB, dedicated
[*] Motherboard -- ASUS P4P800 (I think, anyway; that's what the manual says, anyway)
[*] I can't recall what all software that I've installed since upgrading.  Nothing like Automatrix or any other configuration software, though.  Just things like KTorrent, a dictionary program, Irssi.  I did install Envy after having installed 7.04, though.
[*] Other things I can think of:[LIST]
[*]All the power settings I could find are set to do nothing.  I was afraid that power management stuff might have been the culprit, so I turned off everything of that sort I came across, namely monitor shutoff, harddrive shutoff, and computer suspending.
[*]When I said I first installed ubuntu last summer, I was probably wrong; I am certain that it was Dapper that I installed, and that my problem started before Edgy had been released, so it was probably the summer before last (that is, summer 2006).
[*]The lockup problem will also happen on live CDs.
[/LIST]
[/LIST]

---

### Post by gobbles414 on 2007-12-23
Hey Junction,

No worries about your reply time! The most important information that you have given me is that, "The lockup problem will also happen on live CDs." While the cause of your problems could be any number of things, my best guess right now is to agree with you that it's a video driver issue. You say that you've tried "different video drivers". Does that include any from the *Restricted Drivers Manager*?

---

### Post by Junction on 2007-12-23
Yup, in fact, I'm currently using the restricted driver.  The Restricted Drivers Manager lists just one entry, the ATI accelerated graphics driver, enabled and in use.

---

### Post by gobbles414 on 2007-12-24
Junction,

If you don't mind possibly losing 3D acceleration, try reconfiguring your graphics by doing the following:

*Press escape as your computer is booting. This will bring you to the GRUB menu.
*Select *rescue mode* for the newest version of the Linux kernel.
*Type *dpkg-reconfigure xserver-xorg* and press *Enter*.
*Hopefully, the "wizard" will automatically detect your hardware.
*Once the wizard has completed, type *reboot* and press *Enter*.
*Allow your computer to boot normally.
*If you are not greeted by a warning screen as Ubuntu loads, your reconfiguration has been successful.

---

### Post by Junction on 2007-12-24
Sounds like a plan!  Went through the wizard successfully (a couple of times, actually, but now I'm more familiar with my monitor than before the experience :) ).  I'll try to leave my computer on as much as I can tonight and tomorrow, to see if it'll act up.

---

### Post by Junction on 2007-12-24
Drat, froze up twice in the past hour.

---

### Post by gobbles414 on 2007-12-25
Junction,

Well, let's go to the next step. You say that the LiveCD of Ubuntu 7.10 (GNOME) also locks up. Is it possible for you to make LiveCDs for Xubuntu 7.10 (Xfce) and/or Kubuntu 7.10 (KDE)? I would like to establish whether or not this is a GNOME-based problem. If the Ubuntu LiveCD is the only one to freeze, then I say that you are likely experiencing a GNOME-based problem. Switching to Xubuntu or Kubuntu should solve your problem. However, if either Xubuntu or Kubuntu freeze as well, then it is a problem deep within the operating system itself.

---

### Post by Junction on 2007-12-30
Didn't have much time this week to spend on this computer, but finally got enough info to post.  Since I had tried Xubuntu 7.04 in the past, I figured I'd go with Kubuntu (7.10) this time, but after having used it for a while, experienced similar freezes.

---

### Post by gobbles414 on 2007-12-31
Junction,

Hmm... Does your BIOS have any power saving options? If so, disable them. You might also wish to check for known issues similar to yours on [Launchpad]("https://launchpad.net/ubuntu").

---

### Post by gobbles414 on 2008-01-09
Junction,

Have you made any progress with your freezing problem?

---

### Post by Junction on 2008-01-12
Afraid not.  I've tried a few more things, but I've kinda hit a stumbling point.  I'd rather not mess with the hardware or BIOS at all without having some idea as to what the problem is, as that seems like a very good way to mess things up even more.  However, that seems to leave me somewhat lacking in options.

I should be able to borrow the use of another computer in a few days, so I hope to install PuTTY on that machine and try to remotely watch for the problem.  Hopefully that will yield some results.

---

### Post by Junction on 2008-01-25
Well, the remote debugging plan when horribly awry, with a lot of small setbacks getting in the way (trouble figuring out putty, switched to using a live CD on that computer but it didn't want to recognize the network, that sort of stuff).  However, that became moot earlier this week, as my video card started dying on me!  (Weird screen artifacts, lines covering the screen, that sort of thing, appearing on the screen as early as the bios).  So a bit of diagnosing and shopping later, and now I've got a new video card.

It's been a few days since then, and I figured I'd try to log some time in ubuntu to see if it's still locking up with the new card.  It's been a few hours now; so far, no lockups.  I've had longer streaks before, so it's not conclusive, but it looks promising so far.

---

### Post by gobbles414 on 2008-01-26
Junction,

It makes a lot of sense to me that your old video card was causing Ubuntu to freeze. All sorts of Linux drivers versus Windows drivers issues to consider... By the way, did you check on the internet to be sure that your new video card is compatible with Linux? That is a very important step to do, as certain video cards don't always "play nice" with Linux. After your PC has been in Ubuntu for awhile, please post your results to this thread.

---

### Post by Junction on 2008-02-09
I haven't be able to log as much time as I'd like on my computer lately, but after about 12 hours of combined usage, it's been stable.  Lots of other little problems cropping up, but that's probably just from having switched hardware (though I fail to see why changing my video card would wreck havoc with things like my audio, but I've been working through them).

I didn't research the card online, as I didn't really have a computer to do that with, but it's an nvidia, so I'm not too worried.  So long as it stays running, it'll be an upgrade from before :)

So yeah, I'd say my problem is pretty much solved.  Thank you very much for the advice while I fiddled with this problem.

---

### Post by gobbles414 on 2008-02-13
Junction,

I'm glad to learn that your problem has been solved. I'll check back here periodically, just in case you'd like to troubleshoot your "little" problems.

---

### Post by photismos on 2008-02-22
...tentatively solved would have been a better selection of words for the previous post =D...having similar problems I learned that ACPI causes more than a few wierd random/intermittent errors so I'm going to post this solution here too that I've posted as reply in a few other "Gutsy Gibbon Freezing" threads:  

I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

