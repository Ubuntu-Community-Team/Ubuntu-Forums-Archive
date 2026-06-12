---
title: "Booting into Purple Screen - How To Recover System?"
date: 2013-12-21
forum: General Help
---

### Post by skyesharica on 2013-12-21
Hi, sorry if this is basic, but I can't find an answer anywhere in the documentation or community.

I simply boot into a purple screen.  It has boot options ... about four ... one of them is 'recovery mode'.

Twice I just selected recovery mode.  Text passed over the screen, and I was asked for my *user name* and *password*.  (It wasn't exactly the same both times.)  [U]Then the screen went black and nothing happened.  So I shut down the PC with the button.  Then I started it again, and IT WORKED.

PHLLLEEEAAAZZZ tell me if I am blowing up my PC at Xmas!  

What am I suppose to do at this screen?  It's probably BASIC.  :confused:

---

### Post by mörgæs on 2013-12-21
Please begin with a complete hardware description.

Which versions of Buntu are you trying?

---

### Post by skyesharica on 2013-12-21
> **mörgæs said:**
> Please begin with a complete hardware description.

Which versions of Buntu are you trying?

Thankyou very much and Merry Xmas, early.

Ubuntu Version:  12.04 LTS
Memory:  3.7 GiB
Processor:  Intel® Core™ i3-2375M CPU @ 1.50GHz × 4 
Graphics:  Unknown
OS Type:  64-bit
Disk:  488.2 GB

---

### Post by mörgæs on 2013-12-21
And the graphics card? Please run **lspci** and post the results.

---

### Post by skyesharica on 2013-12-21
[B]I got this:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
09:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)


[/B]

---

### Post by mörgæs on 2013-12-21
> **skyesharica said:**
> 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


I don't see anything strange here. Everything looks fine. 

Maybe someone else can get a step further using the information above. I can only wish you a merry Christmas.

---

### Post by skyesharica on 2013-12-21
So, do you have any idea what I SHOULD DO if I see this screen?  Should I click on the first option or the second option called the "recovery mode"?

Thankyou so much 4 trying.  BEST XMAS OF ALL 2 ALL GUD FOLKS.  :D  :D  :D

---

### Post by Mark Phelps on 2013-12-21
It's been a long time since I used Recovery Mode, but from what I recall, it puts you into a text-mode command prompt -- know as a Command Line Interface (CLI).  Usually, there were some options presented, one of which was to repair broken packages -- which is the one I always chose. After that, I rebooted and the logon screen came up as usual.

If you are able to login now, whatever was wrong has been fixed.

---

### Post by skyesharica on 2013-12-21
> **Mark Phelps said:**
> It's been a long time since I used Recovery Mode, but from what I recall, it puts you into a text-mode command prompt -- know as a Command Line Interface (CLI).  Usually, there were some options presented, one of which was to repair broken packages -- which is the one I always chose. After that, I rebooted and the logon screen came up as usual.

If you are able to login now, whatever was wrong has been fixed.

Hi Mark ... I remember you!  Thanks.

The screen is called the GNU GRUB screen.  This is exactly what it says.:
____________________________________________________________________________________________

GNU GRUB version 1.99-21ubuntu3.10

Ubuntu, with Linux 3.5.0-44-generic
Ubuntu, with Linux 3.5.0-44-generic (recovery mode)
Previous Linux versions
Memory test (memtest 86+)
Memory test (memtest 86+), serial console 115200

Use the arrow keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a  command line.
____________________________________________________________________________________________

[ATTACH=CONFIG]248781[/ATTACH]

A command line is USELESS to me, as I know ABSOLUTELY NO PROGRAMMING.

Do you think I should boot up the first version, or the second option called 'recovery mode'.  I HAVE A STRONG FEELING I AM SUPPOSE TO SELECT THE FIRST OPTION (3.5.0-44-generic)???
As I said - I tried 'recovery mode' twice ... gave a user name and password, the screen went black, I turned it off and on again and it went fine.  Do you have any idea what this means please?

I've read this article about recovery mode ... and I think it is for more advanced users, who know some commands.:  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by jim_deadlock on 2013-12-21
My Ubuntu sometimes doesn't boot properly, I just hit the reset button and it boots fine 2nd time - I think it's because my SSD is too fast or something. Anyway I've never seen any adverse effects of rebooting, I wouldn't worry about it as long as you can get to your desktop one way or another.

---

### Post by skyesharica on 2013-12-21
> **jim_deadlock said:**
> My Ubuntu sometimes doesn't boot properly, I just hit the reset button and it boots fine 2nd time - I think it's because my SSD is too fast or something. Anyway I've never seen any adverse effects of rebooting, I wouldn't worry about it as long as you can get to your desktop one way or another.

Thanks Jim.  That's a big relief.  I'll relax about it.  [COLOR=#800080][SIZE=4]**MERRY XMAS. **[/SIZE][/COLOR]  :KS

---

### Post by grahammechanical on 2013-12-21
Hi,

First of all the first option in the Grub menu will try to boot you into Ubuntu just as if you allowed Grub to finish its count down. The second option should present you a Recovery menu with these options.

> Resume - resume normal boot
Clean - try to make free space.
dpkg - repair broken packages
failsafeX - run in failsafe graphic mode
fsck - check all file systems
grub - update grub boot loader
network - enable networking
root - drop to root shell prompt
system summary - system summary.


But you are not getting that menu. Correct? What you are getting is a Linux command line. Which is why you are asked to log in. Ubuntu sits on top of Linux but it is not loading. When Ubuntu loads it logs us into Linux and then loads the desktop where we first login as a user.

At that command prompt you can run commands just as if you we using a terminal. Useful commands

```
 sudo shutdown -h now
```

Shuts down the machine. It may be more gentle that hitting to power button. 

```
sudo shutdown -r now
```

Reboots.

These commands may get you to a working desktop.

```
sudo apt-get install dconf-tools
```
```
deconf reset -f /org/compiz/
```
```
setsid unity
```

If you can get to a working desktop then I suggest you try changing video drivers. Just a guess.

Regards.

---

### Post by skyesharica on 2013-12-21
> **grahammechanical said:**
> Hi,

First of all the first option in the Grub menu will try to boot you into Ubuntu just as if you allowed Grub to finish its count down.

Great and hi again - I remember you, Graham.  ):P  So if I get this screen, it is best to pick the first option .... and then I will just boot normally ... is that correct?

 > **grahammechanical said:**
> The second option should present you a Recovery menu with these options.

But you are not getting that menu. Correct? What you are getting is a  Linux command line. Which is why you are asked to log in. Ubuntu sits on  top of Linux but it is not loading. When Ubuntu loads it logs us into  Linux and then loads the desktop where we first login as a user.

At that command prompt you can run commands just as if you we using a terminal.

Yes, I *did* get this screen, and I clicked on "Resume - resume normal boot".  Then I was asked for my user name and password, and then it went black and froze.  I think the screen was waiting for a command, and I shouldn't have been in there anyway.  SO WILL I JUST USE THE FIRST OPTION IN THE GRUB MENU INSTEAD?

> **grahammechanical said:**
> Useful commands. ... Regards.

Thanks 4 that but I'll never be able to do programming.

> **grahammechanical said:**
> First of all the first option in the Grub menu will try to boot you into Ubuntu just as if you allowed Grub to finish its count down.

Sorry to ask again, Graham, but ...

what if I just use the first GNU GRUB menu option?:

Ubuntu, with Linux 3.5.0-44-generic

WILL IT THEN BOOT UP AS NORMAL ... is this the normal way to recover a crash of some kind?  Hope that is simple enuf![CENTER][SIZE=7][COLOR=#4b0082][FONT=palatino linotype]
MERRY XMAS[/FONT][/COLOR][/SIZE]   :popcorn:
[/CENTER]

---

