---
title: "Novice Seeking Knowldege On Linux and Dual boot with XP Pro"
date: 2006-10-19
forum: General Help
---

### Post by Junaith on 2006-10-19
[CENTER]_Computer Specs_[/CENTER]

1. CPU – PII 300MHz
2. RAM – 384MB SD-RAM
3. HD - 80GB Seagate attached via a PCI SATA Controller Card to the IDE port in the card
4. Sound card – SB16 or AWE compatible connected via ISA Slot

Hi friends,
The above said are my computer specs. I would like you guys to help me with a few things for my Linux installation please. Many thanks in advance.



1 Currently I am running WIN XP Pro and its works fine. I would like to dual boot Linux with my XP. Please advice me the best, the latest and the easiest distro to use with my ‘old computer specifications’. How much space will I need to run programming, business, servers and multimedia functionality and which distro offer all these functionalities?

My intention is to divide the 80GB into four or more partitions. E.g WinXP 25GB, Linux 15GB, other two or more partitions to hold data, which can be accessed and manipulated by both XP and Linux. Should I create all these partitions in Windows XP prior to installing Linux or leave the remaining 65GB after installing WinXP for Linux to play with. Please also advice what sort of file system to use to play with both XP & Linux to play with one system from the other and common data like mp3.

2. Using Linux I would also like to connect to my Windows network, can it be done using NetBEUI/NetBios? Please tell me how to do this.


3. Up to now I have tried various live CDS, (Mandriva 2006 One, Knoppix, DSL, PCLinux OS, Ubuntu) but I have never been able to listen to any music so far. Is this because the SoundCard is the ISA type?


4. Since my HDD is connected via the Controller card (VIA - VT6421)will there be any problem installing Linux or dual boot?

a) where can I get the Linux driver for this card and how to install the driver while istalling Linux?



***** 5.In Ubuntu-6.06.1 Dapper Drake Live CD - my Logitech serial mouse doesn't work eventhough the mouse's arrow key is on the desktop it doesn't move.**

Please help me solve these problems. 

Thank you very much in advance!!!

---

### Post by ssalman on 2006-10-19
> the latest and the easiest distro to use with my ‘old computer specifications’. 
your ram is okay, but your processor is very slow, try first xUbuntu and see how it works for you, if it is too slugish, you probably want to try pupy linux or DSL (Damn Small Linux)... they are both very small and fast as they were desinged with older machines in mind.

> How much space will I need to run programming, business, servers and multimedia functionality and which distro offer all these functionalities?it depends on the distro, a typical xUbuntu installation requires 1.6GB, so for all the other stuff you'll probably need 2~4 GB just for the basic system and the added applications... on the other hand, DSL basic installation is around 200MB.

> Should I create all these partitions in Windows XP prior to installing Linux or leave the remaining 65GB after installing WinXP for Linux to play with. Please also advice what sort of file system to use to play with both XP & Linux to play with one system from the other and common data like mp3.almost all linux distros will be able to do the partitioning for you during installation. and you'll need to make the shared partitions FAT as this is the best filesystem to share between windows and linux (it is fully supported by both).

>  2. Using Linux I would also like to connect to my Windows network, can it be done using NetBEUI/NetBios? Please tell me how to do this.if you are talking about sharing files, you'll use SAMBA.


>  3. Up to now I have tried various live CDS, (Mandriva 2006 One, Knoppix, DSL, PCLinux OS, Ubuntu) but I have never been able to listen to any music so far. Is this because the SoundCard is the ISA type?if using Xubuntu, try [this]("https://help.ubuntu.com/community/HowToSetupSoundCards") link


good luck.

---

### Post by Junaith on 2006-10-20
Thank you ssalman,
                  for the detailed explanation but pls also say something for the 

***** 5.In Ubuntu-6.06.1 Dapper Drake Live CD - my Logitech serial mouse doesn't work eventhough the mouse's arrow key is on the desktop it doesn't move.** issue.

Thanks!

---

### Post by aysiu on 2006-10-20
Like ssalman, I'm going to recommend Xubuntu. It doesn't matter if it's Xubuntu Edgy (6.10), which will be released next week, or Xubuntu Dapper (6.06), the current release. What matters is that you use Xubuntu, which is relatively lightweight (as opposed to Kubuntu or Ubuntu, which are heavier).

For partition planning, please read this link:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

For dual-boot set up, use the **Alternate CD** and read this:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

With your processor speed and RAM, I don't think the **Desktop CD** approach is the wisest. If you do use that CD, though, this guide will help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Crashmaxx on 2006-10-20
> **Junaith said:**
> [CENTER]_Computer Specs_[/CENTER]

1. CPU – PII 300MHz
2. RAM – 384MB SD-RAM
3. HD - 80GB Seagate attached via a PCI SATA Controller Card to the IDE port in the card
4. Sound card – SB16 or AWE compatible connected via ISA Slot...

...Currently I am running WIN XP Pro and its works fine....

You are running XP on a PC with a 300MHz PII, and it runs **fine**! Please elaborate on how fast it runs and how you achieved this. I have recently messed with old Pentium-MX, PII, and PIII machines, and none of them could even run 95 or 98 at a speed I would find usable or acceptable. And using PC's with 800MHz to 1.6 GHz, XP was slow and annoying, but usable. And only on a 3.0GHz AMD PC could I get XP to run at a fast speed, matching my Ubuntu PC with a PIII 800MHz chip, somewhat ironically.

So, just wondering how XP is for you on such a slow PC. And I have to say, Xubuntu would run great on it. You have enough ram, and that is what linux really needs to run smoothly. I wouldn't say its a ram hog, but more that processor speed is not as big a performance killer as it is for windows usually.

Try the Xubuntu Live CD first thing, it will be much slower then a hard drive install, but if it loads and runs good, then your install should be great. If that is too much, Damn Small linux rocks! It works on pretty much anything fast enough to make use of a CD drive. Not my first choice for an OS, but great on slow machines. You wouldn't even guess how slow a PC on DSL really is, you'd swear it was a new top of the line beast.

Anyway, I've rambled on long enough, welcome!

---

### Post by ssalman on 2006-10-20
> **Junaith said:**
> Thank you ssalman,
                  for the detailed explanation but pls also say something for the 

***** 5.In Ubuntu-6.06.1 Dapper Drake Live CD - my Logitech serial mouse doesn't work eventhough the mouse's arrow key is on the desktop it doesn't move.** issue.

Thanks!

I'm sorry, I never ran into any trouble with mices before. I tried USB and PS/2, but not serial.... the first two options worked on all distros I tried... maybe someone else can help with this one.

But be sure you are using the latest dapper CDs... I found [this ]("https://help.ubuntu.com/community/SerialMouseHowto")wiki page which indicates that older versions had serial mouse problems.... check your CD out to see which version you are using.

Good luck.

---

