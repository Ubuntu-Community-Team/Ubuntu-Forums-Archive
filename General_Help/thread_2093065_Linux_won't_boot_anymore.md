---
title: "Linux won't boot anymore"
date: 2012-12-09
forum: General Help
---

### Post by cbstryker on 2012-12-09
Hi guys,

So recently I upgraded my video card from a Radeon HD 6580 to a Radeon HD 7770. Ever since doing that I can't boot Linux anymore.

I had an existing installation of Ubuntu 12.04 that will boot to the login screen, but once you log in with any user it just goes to a completely blank screen that just shows the background and nothing else. I can open a terminal with ctrl+alt+t and then start programs such as firefox, but there's no window manager. Trying to manually replace my window manager just generates a huge list of errors.

I'm also able to switch to another terminal and do anything from there. So the first thing I did was reinstall the proprietary AMD graphics drivers, but no change.

I've since downloaded Ubuntu 12.10 and Mint 14 but with everything else I only get a black screen and nothing else. The only Live CD that let me do anything was Mint 14 (Cinnamon edition), even thought it showed a blank screen I was able to switch to a terminal and do a dmesg output: [http://imgur.com/IdODv]("http://imgur.com/IdODv")

I'm truly at a lose as to what I can do to get up and running. All distros I've tried are 64bit. Also, "nomodeset" doesn't make a difference on boot.

System Specs:
AMD Phenom II X6 1090T
MB: 990FXA-UD3
RAM: 16GB DDR3
VC: Gigabyte (GV-R7770C-1GD) Radeon HD 7770


Edit: While the issues with booting started after installing a new video card, I don't think it has anything to do with it directly. There's something else going on. Please see the included link to see the boot messages. It's not video card related.

---

### Post by thnewguy on 2012-12-09
Can you boot into Ubuntu 12.04 and run the jockey command? It should let you download the non-free Radeon driver. That fixed my video issues.

---

### Post by apochry on 2012-12-09
If the jockey doesn't do the job you could try to manually install the proprietary graphic driver following the instruction in this [wiki]("http://wiki.cchtml.com/index.php/Ubuntu#Installation").
I needed to do so for my HD6600 card in order to get the 3D Unity to work.

---

### Post by cbstryker on 2012-12-09
> **thnewguy said:**
> Can you boot into Ubuntu 12.04 and run the jockey command? It should let you download the non-free Radeon driver. That fixed my video issues.

I don't think I'm having video specific issues. I've installed the AMD proprietary drivers and it did nothing.

---

### Post by cbstryker on 2012-12-10
> **apochry said:**
> If the jockey doesn't do the job you could try to manually install the proprietary graphic driver following the instruction in this [wiki]("http://wiki.cchtml.com/index.php/Ubuntu#Installation").
I needed to do so for my HD6600 card in order to get the 3D Unity to work.

I already installed the proprietary drivers, I mentioned that in the OP.

Also, that doesn't help if I'm trying to re-install anything from scratch. I can't even get past the grub menu. It just hangs.

---

### Post by cbstryker on 2012-12-12
*******bump********

Anyone have any suggestions?

---

### Post by cbstryker on 2012-12-16
I really could use some insight here. Anyone with any sort of help?

---

### Post by Jvdy on 2012-12-16
if it no video driver issue i think maybe it is your compiz configuration does not match with your current video graphic
have you tried customize your ccsm ?

---

### Post by cbstryker on 2012-12-18
> **Jvdy said:**
> if it no video driver issue i think maybe it is your compiz configuration does not match with your current video graphic
have you tried customize your ccsm ?

No, this doesn't help me with installing Linux.

---

### Post by cbstryker on 2012-12-21
*********bump**********

No help?

---

