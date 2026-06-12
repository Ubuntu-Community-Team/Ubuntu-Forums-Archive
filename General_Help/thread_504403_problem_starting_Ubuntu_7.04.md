---
title: "problem starting Ubuntu 7.04"
date: 2007-07-19
forum: General Help
---

### Post by Guy Terreault on 2007-07-19
Hi, I need help

I have a two OS 
	- Ubuntu 7.04
	- Windows XP

when I start my pc

 I get 
	1- Ubuntu, Kernel 2.6.20-16-generic
	2- Ubuntu, Kernel 2.6.20-16-generic (recovery mode)
	3- Ubuntu, Kernel 2.6.20-15-generic
	4- Ubuntu, Kernel 2.6.20-15-generic (recovery mode)
	5- memcheck

	6-windows XP

	when I choose the first or de third

	I get the ubuntu logo and the status bar shoing that the lodding has started

	but after the first 1/4 inch it stops and nothing happends

	de second and fourth choises are recovery modes
	I get about a page of OKs

	and this message that repeats it self non-stop

	ATKBD,C: spurious ACK on isa0060/serio0 some program might be trying to access hardware
	directly

	yesterday every thing worked fine

	today in Windows I have installed GENIE BACKUP MANAGER 7.0
	I made a backup of some folders in windows

	later I My internet provider went down for 2 hours. At first I did not know that
	so to check if the problem was not on my side. I restarted my computer to see
	if I could access the Net in Ubuntu that's when I found that i could not get in

	Can I fix this whitout reformating...

Thanks in advance...
 Guy

---

### Post by PlatinumPlus on 2007-07-19
If your press Alt + F1 do you get anything?

---

### Post by dragonwings on 2007-07-19
maybe xorg is messed  up 

try starting in rcovery mode let it do its thing then type command below
sudo dpkg-reconfigure xserver-xorg

use arrow,space and enter keys to navagate

if ya not sure what to pick just keep pressing entre or right arrow then enter

good luck

---

### Post by Guy Terreault on 2007-07-19
Thanks Guy for your help

But I can't follow-up on your suggestions

sorry I am an impulsive guy. I tried  2 suggestions about fixing the GRUB
they did not work so I backed  up my important data on windows and Ubuntu
And formated the hd. Now I have a clean window and Ubuntu. 

This gave me the a chance to change the size of my partitions.

Now All I need is a good application in Ubuntu to make a backup of It's partition.

 So Problem solved ???

thanks again
  Guy

---

### Post by strabes on 2007-07-19
That was an agressive way to solve that simple problem. Anyway, try using sbackup.

---

