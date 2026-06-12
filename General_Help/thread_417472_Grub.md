---
title: "Grub"
date: 2007-04-21
forum: General Help
---

### Post by matmar on 2007-04-21
I need your help to resolve the following problem.

I had two partitions - WINDOWS and UBUNTU (Linux).

I had grub to select the operating system during startup.
The 1st one (default) was WINDOWS.

I decided to delete the Linux partition while I am running WINDOWS.

The Linux partition is deleted and when I restart my laptop, it 
stops at GRUB>.

Before that it shows:

GNU GRUB Version 0.95
Minimal Bash-like line edition is supported....


I need your help to use WINDOWS at startup.

Thanks for your help.

Mathewos

---

### Post by Rinzwind on 2007-04-21
Use your windows CD to go into recovery mode
On the C:> prompt type
fixmbr


That restores the windows boot.

Btw: you should ask this on a windows forum ;)

---

