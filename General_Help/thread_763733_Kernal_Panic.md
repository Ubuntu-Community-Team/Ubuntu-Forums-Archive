---
title: "Kernal Panic"
date: 2008-04-23
forum: General Help
---

### Post by Comhra on 2008-04-23
This may be posted in the wrong section and for that I apologise, it's just that I can't find the Hardy forum since the site was reorganised.

Folks, I've taken the plunge and installed the RC.  

Unfortunately, I've had two kernal panics in the space of an hour.  It's never happened before and I'm not sure what the implications are or how serious a problem it is.

Any advise as to how to deal with it would be appreciated.  Maybe I should download the final tomorrow and re-install.

In the meantime, is there anything that I can do?



Hardy looks great.  It's sure to be a winner and FF 3 is the fastest browser I've ever used barring none and including Safari 3.1.

:cool::cool::cool:

---

### Post by bingoUV on 2008-04-23
Hardware details? Most importantly 
1. Graphics card
2. Wireless network card?

---

### Post by Comhra on 2008-04-23
Sony Vaio vgn-n11s/w Duo Core
I.6 Gb
1 Gb Ram

**HD:** Sata, 100 Gb

**Videocard:**

Vendor: &#8206;Intel 810 and later

Description: &#8206;

Media class: &#8206;DISPLAY_VGA

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;2

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x27a2

Sub vendor ID: &#8206;0x104d

Sub device ID: &#8206;0x8212

Misc
Module: &#8206;Card:Intel 810 and later




**Sound Card:**
Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;I/O Controller Hub High Definition Audio

Media class: &#8206;NOT_DEFINED

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;27

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x27d8

Sub vendor ID: &#8206;0x104d

Sub device ID: &#8206;0x8212

Driver
Module: &#8206;snd-hda-intel



**INTERNET**

Vendor: &#8206;Marvell Semiconductor Inc.

Description: &#8206;Fast Ethernet Controller

Media class: &#8206;NETWORK_ETHERNET

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;2

PCI device #: &#8206;0

PCI function #: &#8206;0

Vendor ID: &#8206;0x11ab

Device ID: &#8206;0x4351

Sub vendor ID: &#8206;0x104d

Sub device ID: &#8206;0x8212

Misc
Module: &#8206;sky2

**Wireless**


Identification
Vendor: &#8206;Intel Corporation

Description: &#8206;PRO/Wireless 3945ABG

Media class: &#8206;NETWORK_OTHER

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;6

PCI device #: &#8206;0

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x4222

Sub vendor ID: &#8206;0x8086

Sub device ID: &#8206;0x1051

Misc
Module: &#8206;ipw3945

---

### Post by bingoUV on 2008-04-23
Seems to be well supported hardware. No idea what could cause your kernel panics. Did you install anything except from ubuntu repositories?

---

### Post by Comhra on 2008-04-23
Nothing other than the Ubuntu Restricted Extras from Add/Remove and Smartmontools from Synaptic and neither of these is likely to cause a problem.

Everything is working including my SDHC Card :) and very few Distros will recognise the large capacity ones.

Two things:
1) I'm Dual-booting with PCLOS and I know that Ubuntu modified the MBR accordingly.

2) It happened after I rebooted in order to properly install the updates and again after I added an extra Dictionary in Language Support.

Therefore it seems to be an update problem as far as I can tell.

Like I say, I've been using Ubuntu since Feisty and this is the first time this has happened.

What I'd like to know is how serious is a Kernal Panic?

I hope it doesn't mean that I can't use Hardy Heron.

---

### Post by Comhra on 2008-04-23
Hi folks

Discovered that I have a big Spindown issue with PCLOS.  Installed Smartmontools in Ubuntu, ran the command:sudo smartctl -a /dev/sda | grep Load_Cycle_Count, compared the result to what it was before I uninstalled Gutsy ( was going to try the Beta and changed my mind and put PCLOS on instead 4 weeks ago.)

Big problem!

Applied the hack that I found to fix the issue in Gutsy, still works in Hardy.  I've monitored Hardy carefully after fixing the 'Spin-down' and I know that this is not an Ubuntu related. 

This means that I can't dual-boot.  PCLOS is a great Distro, I'll be sorry to see it go, but there is no other choice.

It doesn't suit this laptop.

Why don't I ask at the PCLOS forum?

Hmmm...

---

### Post by bingoUV on 2008-04-23
Kernel panic is very serious. You should not use a system if you know it causes kernel panics frequently. Possible effects : 
1. You lose all your unsaved work, get distracted, waste time in waiting for it to boot again. 
2. Sometimes, files that you thought were written to hard disk will not be written completely and could cause surprising results.

Though if it is only a fun / entertainment / casual use machine, you might be able to live with it.

---

### Post by Comhra on 2008-04-23
Hi Bingo,

Thanks for the help.  Got rid of PCLOS, reinstalled Ubuntu, updated, rebooted, no kernal panic, installed the same language pack as before and rebooted as required, still no kernal panic.  I'm keeping my fingers crossed and I do hate loosing PCLOS but it was obviously causing problems.  

I'm going to mark this one as solved.

---

### Post by Comhra on 2008-04-23
All is well, now if Man U can just grab a goal...

Keep your fingers crossed.

:):):)

---

### Post by Comhra on 2008-04-23
Well, Man U managed a draw away from home which is a good result considering that they were totally outplayed.

As for Hardy Heron...

Wow!

;)

---

