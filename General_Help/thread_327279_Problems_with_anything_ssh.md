---
title: "Problems with anything ssh"
date: 2006-12-28
forum: General Help
---

### Post by Copperblade on 2006-12-28
Hey guys, I just wanted to check here before submitting a bug report:  is anyone else having trouble with ssh protocol on Edgy?  My guess is no, since I can't find anyone talking about it online.  The problem is this:

Whenever I ssh (or scp, or rsync, same port) a significant amount of bandwidth (unmeasured), the machine completely locks up.  If I simply *use ssh* normally via a terminal, I have no problems.  But as soon as data starts transfering fast, I get completely locked up and have to push "reset" on the machine.  For example, it locks up when:

* I try to copy something remotely using scp
* I try to copy something remotely using rsync
* I have a lot of text scrolling in my terminal (using ssh) when connecting to the machine remotely

I've also noted that using rsync locally from one drive to another does NOT lock up the machine.  (I'm not sure if rsync is smart enough not to use ssh in this case).

I've been looking around online and have seen lock ups with ATI cards mentioned.  Both machines I have tested this on have old ATI cards, for example one is an ATI Rage 128, so I don't think that is it.

Any ideas?

---

### Post by kd7swh on 2006-12-29
Do you have the same problems with PuTTY or Grsync? (Graphical Clients) I know that older ATI cards tend to lock up systems due to bad drivers. How well does it work outside of X?

---

### Post by Copperblade on 2006-12-29
> **kd7swh said:**
> Do you have the same problems with PuTTY or Grsync? (Graphical Clients) I know that older ATI cards tend to lock up systems due to bad drivers. How well does it work outside of X?

It doesn't seem to matter how I connect to the machine, even PuTTY on Windows will lock up the Linux machine if I have too much data being transferred over ssh.  

I just tried shutting down X and scping a file... and it froze right away.

---

### Post by kd7swh on 2006-12-29
that is very strange. It could be the ATI card, but it doesn't really add up. What are the system specs? is it a slow computer? Is it a networking issue? (bad routing or switching maybe?)

---

### Post by Copperblade on 2006-12-29
> **kd7swh said:**
> that is very strange. It could be the ATI card, but it doesn't really add up. What are the system specs? is it a slow computer? Is it a networking issue? (bad routing or switching maybe?)

It's a machine that didn't have this problem when I was running Debian ;).  (I'd like to not have to go back to Debian--they're a bit particular on the openness of their packages.)

Linux pascal 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006
One Intel Pentium III (Coppermine) 731MHz processor, 1464.98 total bogomips, 319M RAM
System library 2.4.0

Bus:
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
00:0d.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
00:0f.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

But I don't think that it's a hardware problem really.  I am having the exact same problem on my Laptop that's running Edgy also.  I only mentioned ATI because that's the only common hardware between the two:  ATI graphic sets, and because I saw mention of ATI lock ups in the bug tracker.

I'm also running a Windows machine with no apparent problems, and a Debian server with no apparent problems.

But if I'm the only person in the world having this problem, I can't imagine why.

---

