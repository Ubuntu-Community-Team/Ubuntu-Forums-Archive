---
title: "LiveCD will not boot all the way"
date: 2020-06-15
forum: General Help
---

### Post by historyb on 2020-06-15
Hello,

I am having a bit of a problem. I received a computer a while back and wanted to put Linux on it, all was good. At least I thought all was good, when the computer booted the grub screen appeared than went blank and stayed that way. After searching I tried using safe graphics mode and it worked. I installed Ubuntu proper and every time I booted the computer I had to append grub with "nomodeset". I really don't know what to do, I am at an impasse and right now I have windows which I absolutely don't want to have installed but I don;t know what to do. Here is my pertinent info about my video card:

Radeon hd 6550d 

I even tried additional drivers or restricted drivers tab but it came back with no additional drivers, maybe I did something wrong. I am sorry to brother everybody I just needed so more help.

I tried Ubuntu 18.04 and 20.04

---

### Post by CelticWarrior on 2020-06-16
AMD graphics should work, shouldn't need nomodeset.

Have you perhaps installed in legacy mode in a new UEFI PC?

---

### Post by historyb on 2020-06-16
> **CelticWarrior said:**
> AMD graphics should work, shouldn't need nomodeset.

Have you perhaps installed in legacy mode in a new UEFI PC?

Hi,

Thank you for the help. I checked the BIOS and it is in UEFI mode. Not even the LiveCD will boot but will get to grub unless I use nomodeset and it happens on every variant of Linux Distro's I tired so far like PCLinuxOS, Manjaro, Linux Mint, Elementary OS among others.

---

