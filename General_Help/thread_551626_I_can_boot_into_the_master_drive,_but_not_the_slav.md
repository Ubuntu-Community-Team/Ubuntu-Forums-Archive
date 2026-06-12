---
title: "I can boot into the master drive, but not the slave"
date: 2007-09-15
forum: General Help
---

### Post by Boris and Bailey on 2007-09-15
Any suggestions out there on how to get two disks, one Ubuntu, the other Windows XP, to boot upon given the choice? I have tried two different configurations, one with Grub with Ubuntu as the master disk, the other with WinGrub with Windows as the master disk, In both scenarios, I can only boot into the master disk, but not the slave disk.


SCENARIO ONE:

Master disk: Ubuntu
Slave disk: Windows XP

In menu.lst, I included the following:

title                  Windows XP
root                 (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Everything in Windows was untouched.

This gives me a startup choice between Windows XP and Ubuntu Feisty Fawn. I can get into Ubuntu but not Windows XP.


SCENARIO TWO:

Master disk: Windows XP
Slave disk: Ubuntu

In WinGrub:
Profiles: Dskboot
Windows hd 0,0
Ubuntu hd 1,0 and 1,4

boot.ini:

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\GRLDR="Start Grub"

Everything in Ubuntu was untouched and with no changes to menu.lst.

This gives me a startup choice between Windows XP and Grub. I can get into Windows XP but not Ubuntu.

---

### Post by rivalarrival on 2007-09-15
I take it that you don't want to reinstall either installation? Because there is a TON of stuff on how to do this with a new installation - google Ubuntu Dual Boot and you'll have at least 20 different guides on how to do it.

But with existing installations...

This might be useful:
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

If not, what errors are you getting?

---

### Post by Boris and Bailey on 2007-09-15
Thank you for your response! You're right, there are several articles by quering the search engines. That was my first step. Interesting article you provided a link to. I bookmarked it. True, if I can avoid reinstalling Windows, I will. Ubuntu...maybe.

The error message I got from the Grub configuration (master disk--Ubuntu, slave disk--Windows) was:

Session manager initialization system process terminated 0xc0000013 with the blue screen. Other messages: snd_emu10k1, snd_hda_intel. Despite the ominous first message, I can still boot into Windows provided it is the master drive.

---

