---
title: "Computer reboots by itself - Ubuntu 12.04"
date: 2013-10-28
forum: General Help
---

### Post by rmimtz on 2013-10-28
Good morning everybody.

I am a Linux user for many many years, but absolutely new in the Ubuntu world because I switched to it (Xubuntu 13.10 precisely) a few weeks ago when I received my new computer.

It is a Sager-Clevo NP-2740 (proc: Intel(R) Core(TM) i7-4750HQ CPU @ 2.00GHz) that runs a Dualboot with W7. I almost never use W7, except when I need to run really special softwares that I only have under w7.

I experienced few times a really bothering behaviour when I try to shutdown my computer under Xubuntu. This behaviour happens both with a graphical shutdown (clic-button) or with a command line shutdown (sudo shutdown -h now).

The computer shuts down normally but turns on again by itself after 5 seconds. It is an infinite loop. I log under Xubuntu, try to shutdown again, and bim, it restarts by itself. I need to log under w7 to shut it down properly.

This problem also happened under Mint (before Xubuntu I tried Mint 16, and after a few reboots by itself, I switched under Xubuntu because I thought the problem was coming from Mint).

I did many researches and I found these 2 solutions that were recommanded for Ubuntu 12.04:

** change the grub (quiet splash by nomodeset or by noirq quiet splash);
** install laptop-mode-tool.

The first solution does not work at all.

The second solution works, but creates me so many bugs after (mouse that doesnt work, fonts that become super-small under wdm, and other few strange and bothering things).

Thank you very much for any kind of help (even if you suggest me to throw my computer by the window).

Remi.

##############################################################

Here is the result of lspci:

00:00.0 Host bridge: Intel Corporation Crystal Well DRAM Controller (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08)
00:03.0 Audio device: Intel Corporation Crystal Well HD Audio Controller (rev 08)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

##############################################################

Here is the result of lscpu:

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 70
Stepping:              1
CPU MHz:               800.000
BogoMIPS:              3990.81
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
L4 cache:              131072K
NUMA node0 CPU(s):     0-7

##############################################################

Here is the result of lsblk:

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   350M  0 part 
&#9500;&#9472;sda2   8:2    0 122.9G  0 part 
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  93.8G  0 part /
&#9492;&#9472;sda6   8:6    0  15.9G  0 part [SWAP]

---

### Post by rmimtz on 2013-11-06
Good evening everybody,

I am little by little going forward out of my problem.

As it drove me crazy, I decided to erase windows from my computer (I thought the problem came from the grub) and keep going with only one OS on my machine. At the same time I decided to switch from Xubuntu 13.10 to Ubuntu 12.04, hoping that the LTS will sove my problem. To be clear, I was wrong. Thanksfully I have an official w7 pro licence if I want to re-install the double boot.

Nevertheless, I discovered a few interesting things:

** laptop-mode-tools helps (after some fine tuning to make my USB mouse working properly, etc...);
** my computer only reboots by itself when it is on AC. If I turn it off when it is on battery, it stays off and does not reboot. Which actually changed my life.

After 3 days trying to fine tune  laptop-mode-tools, and after at least 50 turn on/turn off, I dont find where the solution comes from when the computer is on battery. The idea would be to apply the exact same setting when it is on AC.

For the people who are familiar with   laptop-mode-tools, here is the laptop-mode.conf: [https://filex.mat.ensmp.fr/get?k=vvAwbdxw6ZnbmlTTMib](https://filex.mat.ensmp.fr/get?k=vvAwbdxw6ZnbmlTTMib)
I am pretty sure 75% of my problem is solved, but I need help for the last 25% !

Thank to the people trying to help me !

Remi.

---

### Post by jamesisin on 2013-11-06
Is there possibly a setting in your BIOS for automatically starting the machine under certain conditions?

---

### Post by rmimtz on 2013-11-06
Absolutely no idea. I never touched my BIOS. What kind of setting could it be ?

---

### Post by jamesisin on 2013-11-06
Dunno.  Some machines will have a setting, though it's usually for booting when power is restored (like a server which lost power gets power restored and starts automatically).  Just a (long shot) thought.

---

### Post by rmimtz on 2013-11-06
Okay, thank you for the idea. But I dont know either, and as my knowledge about what to do and what not to do on the BIOS is close to zero, I prefer not to play with it !

Does laptop-mode-tools sets something on the BIOS ?

---

### Post by jamesisin on 2013-11-07
I doubt it.  If you do poke around in the BIOS, feel free to ask about any setting you see there.  Unless you save your changes it should be harmless to have a look.

---

### Post by rmimtz on 2013-11-11
Hello,

ok, I am gonna have a look into the BIOS and check if I notice something strange.

Thank you for the advice !

Have a nice day jamesisin.

---

### Post by linuxguru43 on 2013-11-11
Sounds like your power supply is failing.

---

### Post by rmimtz on 2013-11-11
I have no idea what is failing.

What can I do to check if thepower supply is crazy or not ?

The funny thing is that this computer is also sold by System 76 with Ubuntu 13.04 ([https://www.system76.com/laptops/model/galu1](https://www.system76.com/laptops/model/galu1)). They bought it to Clevo and rebrand it System 76.

So a solution must exist, because I doubt they sell a computer that reboots by itself.

---

### Post by linuxguru43 on 2013-11-11
Try switching back to the original desktop environment yet? Unity is what it probably came with from the factory. Does the issue still occur at that point? Great way to test for hardware issues is to create a live flash drive stick of Ubuntu and boot from your live stick of Ubuntu and let it sit. Check the logs on the live stick to see if anything is out of the ordinary. You will know pretty quickly if it is hardware or just a setting that is messed up.

---

### Post by Johan De Cauwer on 2013-11-11
> **rmimtz said:**
> 

The computer shuts down normally but turns on again by itself after 5 seconds. It is an infinite loop. I log under Xubuntu, try to shutdown again, and bim, it restarts by itself. I need to log under w7 to shut it down properly.

This problem also happened under Mint (before Xubuntu I tried Mint 16, and after a few reboots by itself, I switched under Xubuntu because I thought the problem was coming from Mint).
...
Thank you very much for any kind of help (even if you suggest me to throw my computer by the window).

Remi.


So a dual-boot system where you installed multiple OS (more or less the same kind) works perfect under W7 but not under any Ubuntu-like OS and at the same time your're certain that Ubuntu 13.04 can function because in a later post you indicate this computer is sold with 13.04?

Keep your computer. ;-)

The solution must be found in bios. By the way, and I know this is not a solution, what happens if you hit the power switch after those 5 seconds when it wants to reboot?

---

### Post by rmimtz on 2013-11-11
> **Johan De Cauwer said:**
> So a dual-boot system where you installed multiple OS (more or less the same kind) works perfect under W7 but not under any Ubuntu-like OS and at the same time your're certain that Ubuntu 13.04 can function because in a later post you indicate this computer is sold with 13.04?

Keep your computer. ;-)

The solution must be found in bios. By the way, and I know this is not a solution, what happens if you hit the power switch after those 5 seconds when it wants to reboot?

Good evening Johan,

you are abslutely right. W7 was working normally. Zero problem of reboots, ever. And, yes, System 76 sells the same computer with 13.04 distro.

I tried to hit  the power switch after 5 seconds when it wants to reboot, and a quick clic does nothing. The computer restarts alone when on AC. Like a big boy.

I also checked on the BIOS, but as I don't know exactly what to look for, I am a little lost.

Have a nice end of day !

Thank you.

Remi.

---

### Post by rmimtz on 2013-11-11
> **linuxguru43 said:**
> Try switching back to the original desktop environment yet? Unity is what it probably came with from the factory. Does the issue still occur at that point? Great way to test for hardware issues is to create a live flash drive stick of Ubuntu and boot from your live stick of Ubuntu and let it sit. Check the logs on the live stick to see if anything is out of the ordinary. You will know pretty quickly if it is hardware or just a setting that is messed up.

Hello linuxguru43,

> **linuxguru43 said:**
> 
Try switching back to the original desktop environment yet? Unity is  what it probably came with from the factory. Does the issue still occur  at that point?


I am only using Ubuntu 12.04. So I already have Unity. I stopped using Xubuntu to switch to the LTS, hoping that the problem will stop. It was a good idea, but it did not work !

> **linuxguru43 said:**
> 
Great way to test for hardware issues is to create a live flash drive  stick of Ubuntu and boot from your live stick of Ubuntu and let it sit.  Check the logs on the live stick to see if anything is out of the  ordinary. You will know pretty quickly if it is hardware or just a  setting that is messed up.


Stupid question: how can I access these logs ? Is it what the system displays when i turn it off (the black screen with the messages just before the Ubuntu logo) ? Are there stored somewhere, in a file I can cat or vi ?

Thank you and sorry if my questions are stupid.

Remi.

---

### Post by rmimtz on 2013-11-21
Hello everybody;

crazy update on my weird problem:

I discovered that if I unplug the AC cable just in between the moment the computer turns off and it automatically reboots, the computer does not reboot at all. This works with and without laptop_mode enabled. And I also discovered that the reboot problem does not appear on battery when laptop_mode is off.

For those who tried to help me before, I went on the BIOS, and as expected I did not find anything strange. At the same time I did not know exactly what to look for.

Thanks to those involved in that topic that try to help me.

Remi.

---

### Post by jamesisin on 2013-11-21
What you are seeking in the BIOS is a setting which starts the machine when power is restored.  That should give you all the key terms you would need to look through your BIOS and locate the setting in question.  Like I said previously, this settings exists primarily so that if a server loses power (a power failure) the server will restart when the power is restored (to the building).

Can you try a different power supply?  Like perhaps borrowing the same power supply from a friend?  Or visit a store which happens to sell that power supply?

---

