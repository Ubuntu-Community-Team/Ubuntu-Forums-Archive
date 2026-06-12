---
title: "After installing updates last weekend, Lubuntu 12.04 LTS won't boot to login"
date: 2015-09-05
forum: General Help
---

### Post by bowie101 on 2015-09-05
Hi all. Have Lubuntu 12.04 on a NB205 (Toshiba) netbook for many months now. Never a problem. I put in a solid state hard drive in there, and it has worked so well until now. 

Last weekend I updated via the software upgrade tool (I usually update via command line) and since then, I can not reboot. 

now, I push the power button to turn on, and the screen either is blank (but the back light is on, so you know the screen is "on"), or what keeps flashing on my screen (before logon option, before the desktop environment visibly kicks in at all) is   

[FONT=Arial] [FONT=century gothic]```
Stopping save kernel messages [ok]
```[/FONT][/FONT][FONT=Arial][FONT=century gothic]

[FONT=arial]It seems to be caught in an infinite loop.  Flashing that message. 

Help? Suggestions ?[/FONT][/FONT][/FONT][FONT=arial]
[/FONT]

---

### Post by howefield on 2015-09-05
> **bowie101 said:**
> Suggestions ?

Only one that you probably weren't considering.

Lubuntu 12.04 is end of life, might be an opportunity to upgrade to something current ?

---

### Post by bowie101 on 2015-09-05
Was not considering that YET because 

a) i have data on this hard drive (files and what not) that  I want to preserve and not just write over 

b) I installed 12.04 specifically because I read that it worked with my hardware - Toshiba netbook circa 2010. I am more married to the hardware than the software. So I just want to use a linux flavor/distribution/release that I am as certain as I can be won't give me exactly the kind of problem that I now face. 

c) why is it that whenever I use ubuntu, that I am eventually at this exact crossroad? A fresh install or don't use? That's a rhetorical question. I'd like to think that there is a 3rd option.

---

### Post by howefield on 2015-09-05
Try botting into a previous kernel, if you don't get a grub screen at boot up from which to choose options, pressing the shift key whilst booting should display the grub menu.

---

### Post by bowie101 on 2015-09-05
when you say booting into a previous kernal, do you mean, using a USB to boot? Maybe you don't mean that. So I press shift when powering on, I get a grub loading kind of message which i don't recall seeing b4, but that's it. no choice given. Some other lubuntu screen displays, and then a blank screen and that's it.

---

### Post by ajgreeny on 2015-09-05
Nowadays the grub menu only offers you the most recent kernel on the first line, the same kernel but in recovery mode on the second line, and a third line showing **Advanced**.  Choose that and you will get a second menu with a list of kernels of all previous numbered versions in normal and recovery mode.

Choose one of the normal boot style previous kernels from that list, not the first one in the list as that is a repeat of the latest version, and you may be lucky and get to a full desktop.

---

### Post by bowie101 on 2015-09-05
OK, but how do I get the grub menu to make the choice in the first place? It was easy and automatic when I had a dual boot years ago. But now,even though it told me once that grub is loading, I am not given any grub menu choices/options.

---

### Post by howefield on 2015-09-06
> **bowie101 said:**
> OK, but how do I get the grub menu to make the choice in the first place? 

Pressing the shift key when booting should give you the grub screen.

---

### Post by bowie101 on 2015-09-06
Well, no such luck. Got to grub, tried all other previous kernels. No change. Seems to be able to get into recovery mode of at least the previous kernels if not the current one. (didn't actually try that one, so I can't confirm on that.) Able to drop to command line, while in recovery mode. Tried to dpkg to fix packages. Said no packages needed fixing, do I want to start recovery/fixing or whatever? Then I get stuck in there. That's about all I was able to come up with. Yes on previous kernel recovery mode first stage, no on previous kernel boot.

---

### Post by bowie101 on 2015-09-06
As a last resort, If there is a way to save all my data onto an external USB connected hard drive, I have the hard drive to do it. I just don't know how to do that given the state it is in now. Then I would be open to a reinstall. Just need some guidance as to how. Most things I saved on the desktop of the admin user. There was only 1 user.

---

### Post by Bucky Ball on 2015-09-06
> **bowie101 said:**
> As a last resort, If there is a way to save all my data onto an external USB connected hard drive, I have the hard drive to do it.

Can you boot from live media, USB or disk? If so, 'Try Ubuntu', once at a desktop transfer your files to the external storage device. You don't need to be able to boot your installed system to transfer your files. 

There is a way to avoid the crossroad you are speaking of re. upgrading. Upgrade to a new release via the net before the release you are using reaches end-of-life. If you open 'Software and Sources' and click the 'Updates' tab, you will find at the bottom that you can set it to notify you of all new releases or just LTS releases. I suggest 14.04 LTS when you reinstall as Lubuntu 14.04 LTS is supported for three years now (from memory).

You can set it to only notify you of new LTS releases. You can do an 'in-box' net upgrade from LTS to LTS when the time comes (14.04> 16.04 LTS), leap-frogging the interim releases in between. Neat. :)

---

### Post by bowie101 on 2015-09-07
Thanks for the info! Very much appreciated! Before i pull that trigger however, is that where I am at? No other suggestions?

---

### Post by Bucky Ball on 2015-09-07
That's where you're at. Lubuntu 12.04 is no longer supported and does not get updates/upgrades, including security updates. The longer you leave them, the more vulnerable your machine will become. You are also running outdated versions of possibly all software apps.

---

