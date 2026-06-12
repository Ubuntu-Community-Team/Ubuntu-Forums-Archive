---
title: "XUBUNTU Running slow"
date: 2020-06-20
forum: General Help
---

### Post by Mel_Blakey on 2020-06-20
_Dell Latitude E5500_
This machine is 12y/o as far as I know but the mother board was changed (for anther old one) just before I bought it.

When I got this machine 2 months ago I installed the hard drive from another lappy that had Ubuntu 18.04 (with separate Home partition) on which ran like a dream.

It was sluggish on this machine so I installed Xubuntu 20.04. 64 Bit.
Before installing I wiped all of the .Dot files from the Home partition.

Unfortunately, Xubuntu was running slow, and was going slower & slower the longer it is on. To a point where apps refused to close down.

I say was, because yesterday I removed: 'Blueman + Bluetooth adaptors' as there is no Bluetooth card installed. This has made a significant improvement and I feel that I am 70% there in getting this machine running good on Xubutu. 

I feel that this machine should buzz along and if so I need help to get it there.

On a hardware point. Because, I thought that it might be a heat thing. I have reseated the CPU heatsink with fresh compound. It's made no difference to performance.
Things do not seem to be getting too hot anyway.
I have also checked that the HDD is in AHCI mode.

I have also played about with swappiness settings from 20-0

Here is the Specs + The Hard Drive Layout - Thanks! in advance,

2 Gig Ram
Processor Type:    Inter(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz
Core Count:    2
Processor ID    10676
Cur Clock Speed    2.267 GHz

Primary HD    500GB HDD

Bios Version    A17
Memory Insld    2048
Memory Avlbl    2003
Mem Chanl Mode    Dual
Mem Tech    DDR2 SDRAM

--------------------------
HDD INFO:
SATA set as    AHCI

Partition    Type    Filesystem    Mount Pount
/dev/sda1    Primary    grub2 core.img        
/dev/sda3    Primary    ext4        /
/dev/sda9    Primary    ext4        /home
/dev/sda2    Primary    linux-swap

swapiness = 10

---

### Post by HermanAB on 2020-06-21
That machine should work with Xubuntu, but if you can find more RAM so you have 4GB, then that will make a huge difference.

---

### Post by T6&amp;sfpER35% on 2020-06-21
whats the output of **htop **?
i'm also on xubuntu with 3Gb RAM and my machine is FAST (or fast enough lol)

---

### Post by Mel_Blakey on 2020-06-21
Hi **HermanAB**

Thanks for the advice. I was thinking of adding more memory. But, chose this OS based on the system requirements of [B]512 MB of memory.
[/B]I've had re-read it, and it does actually say that, that is the minimum requirement.
It goes on to state:-
[h=2][SIZE=2]Recommended system resources[/SIZE][/h] [I]To get a smooth experience when running multiple applications  parallel on the desktop, it is recommended to have a 1.5Ghz Dual Core  processor with at least **2 GB** of memory.
[/I]
Maybe I should have read it fully! DOH!




> **3nd said:**
> whats the output of **htop **?
i'm also on xubuntu with 3Gb RAM and my machine is FAST (or fast enough lol)

Thanks for your reply.
I'm not sure how to show the full output of **htop** on here but here is the info at the top:-

1 = 20%
2 = 28.4%
Mem: 1.06 / 1.90G
Swap: 27.9m / 12.0G

This is with Firefox running 3 Tabs, 1 of them playing a youtube video.

Do you know why it is using Swap which is set at 'swappiness 10'?

---

### Post by Yellow Pasque on 2020-06-21
> **Mel_Blakey said:**
> Do you know why it is using Swap which is set at 'swappiness 10'?

What were you expecting to happen? That's how virtual memory and swap works. Swap out the stuff you don't need and free up RAM.
In fact, you should probably put the swappiness value at least a little higher on such a system with limited RAM.

---

### Post by Yellow Pasque on 2020-06-21
Oh, and someone else asked how to lighten a Xubuntu install the other day. Here was my response: [https://ubuntuforums.org/showthread.php?t=2445504&p=13965727#post13965727](https://ubuntuforums.org/showthread.php?t=2445504&p=13965727#post13965727)

---

### Post by Autodave on 2020-06-21
3 tabs in FF running and one of them running a video?  You are just about running that equipment at its max.  One suggestion would be to install uBlock in FF.

---

### Post by Mel_Blakey on 2020-06-21
> **Yellow Pasque said:**
> What were you expecting to happen? That's how virtual memory and swap works. Swap out the stuff you don't need and free up RAM.
In fact, you should probably put the swappiness value at least a little higher on such a system with limited RAM.

My understanding was that it started to use the Swap as RAM when it had used 90%. That how I read it.

Thanks for putting me right!

---

### Post by Mel_Blakey on 2020-06-21
> **Autodave said:**
> 3 tabs in FF running and one of them running a video?  You are just about running that equipment at its max.  One suggestion would be to install uBlock in FF.

Thanks. I've been using uBlock for quite a while now!

---

### Post by T6&amp;sfpER35% on 2020-06-21
this is my htop with 2 tabs open one running a youtube vid
[ATTACH=CONFIG]286281[/ATTACH]

and this is htop with one tab open the youtube vid off
[ATTACH=CONFIG]286282[/ATTACH]

you can see the difference especially the cpu 
my swappinnes also at 10
 my advice would also be to add more RAM

---

### Post by Mel_Blakey on 2020-06-21
> **Yellow Pasque said:**
> Oh, and someone else asked how to lighten a Xubuntu install the other day. Here was my response: [https://ubuntuforums.org/showthread.php?t=2445504&p=13965727#post13965727](https://ubuntuforums.org/showthread.php?t=2445504&p=13965727#post13965727)

I searched around before posting and came across your advice to use **systemd-analyze blame** and removed 'Blueman + Bluetooth adaptors' as a result and that has made a big difference.

Thanks!

---

### Post by Mel_Blakey on 2020-06-21
I think the main issue is the missing Bluetooth Adaptor which apps are looking for and not finding. I have remove everything associated with Bluetooth and it seems to have solved the problem.
For an oldie its running quite good.

Thanks for your input guys!

---

