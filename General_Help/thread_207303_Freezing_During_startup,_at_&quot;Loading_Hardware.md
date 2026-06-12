---
title: "Freezing During startup, at &quot;Loading Hardware Drivers&quot;."
date: 2006-07-01
forum: General Help
---

### Post by muffinhead on 2006-07-01
Hello everyone, I am having a problem with ubuntu 6.06 (Dapper Drake) i recieved in the Mail today.

I posted a thread about a month or two ago, relating to breezy, saying how my intel extreme graphics onboard Video, was causing conflict with my PCI Nvidia Geforce FX 5500, and Ubuntu, causing it to freeze at hotplug subsystem. Now that I've upgraded to Dapper Drake, almost the same exact problem, is plagueing me again. 

Well since I got Ubuntu Dapper 6.06, the method of editing the /etc/hotplug/blacklist , to blacklist: intel_agp, agpart, no longer applies in dapper drake 6.06, as there is no hotplug directory, or blacklist file. From what I've heard, the Hotplug has been removed in Dapper Drake 6.06:confused:

It is freezing during startup at "Loading Hardware Drivers", and I believe it may have something to do still with the conflict of the Intel Extreme Graphics, and my PCI Nvidia geforce FX 5500 again:(

I've tried both installing the nvidia drivers, and sudo dpkg-reconfigure xserver-xorg, to use the nvidia driver, and configure xorg to use the PCI Bus my geforce fx 5500 is on, which is 1:1:0 , but nothing seems to work.

I can use my onboard video just fine, with ubuntu, but when I switch to my PCI nvidia Geforce FX 5500, in the bios, it freezes at "Loading Hardware Drivers" when I us Ctrl+C, to skip "Loading hardware Drivers, Ubuntu fails to load "X".

I've booted into recovery mode, using my PCI Video, and it gives me an error "Kernel Panic! Not synching".

If anyone could Help me solve this reoccuring problem again, I'd be so thankful, Thank You;)

Heres a link to [My Other Thread]("http://www.ubuntuforums.org/showthread.php?t=173653") , for futher referance, it's two topics in one, one being the hotplug freezing during startup.;)

My PC Specs as Listed:

Intel Celeron D 330 @ 2.66 GHZ

1024 Megabytes DDR Ram

Sony DRU-810A Dual Layer DVD-RW

Nvidia Geforce FX 5500 OC (PCI)

Creative Labs Sound Blaster Live! 24-Bit

Conexant HSF Softmodem (Reisling Brand, Conexant Chipset)

Main HDD: 120 Gigabytes, Second HDD: 160 Gigabyes, Third HDD: 40 Gigabytes.

Plenty of free hard disk space.

---

### Post by muffinhead on 2006-07-01
bump, can someone please help me, so I'll be able to use ubuntu, Thank You;)

My thread, on the same subject, in the Beginner Talk forum, can be closed. I decided to post it here, so I have less a chance, of my thread being bumped to the fifth page, in a matter of 15 minutes or a half an hour. 

Also I feel by posting here, I'll also recieve a faster, and more efficient response;)

---

### Post by blackjack6.21.91 on 2006-07-01
Well I'm very sorry your not able to start Ubuntu.  Just as sorry I can't help you more.  If you think the nVidia card is causing problems you can just pull it out to start up and debug.

Peace,
blackjack

---

### Post by hornett on 2006-07-02
If you start up in single user/recovery mode, what is the last message you get before the freeze?

BTW: there is a blacklist file which I use, it is located at /etc/modprobe.d/blacklist

hope this helps

---

### Post by mlind on 2006-07-02
Tried booting with acpi=off and noapic flags?

---

### Post by muffinhead on 2006-07-02
Thanks for replying, I really appreciate it, it felt as if I were going to go insane;)

If I boot into recovery mode, with my Geforce FX 5500, I get the error: "Kernal Panic!, Not synching"

If I boot into ubuntu, with my onboard, everything boots up fine, with no problems.

I had an almost same problem with breezy. turned out, my onboard intel extreme graphics 3d, was causing confict, between my PCI Geforce FX. I was able to edit /etc/hotplug/blacklist , to fix the problem, but can no longer do that anymore in Dapper Drake.

I'll take a look at /etc/modprobe.d/blacklist, edit it, and see if it helps. If it does, or doesn't I'll report back here with the results;).

Btw, I want my thread in "Absolute beginner talk", on this same subject, to be closed, as I want to use this thread here in "General Support"

Who would I contact to close my previous thread, on the same subject in "Absolute Beginner Talk"?

---

### Post by muffinhead on 2006-07-02
I'm reporting back:D I just tried editing /etc/modprobe.d/blacklist, and adding:

Intel_agp
agpgart

the same thing I added in breezy badger, and sadly it does not solve my problem. 

I'm hoping someone that has solved this problem, or figured out what to do to solve it, will come and post.

Hasn't anyone figured out how to solve this, or has any possible fixes?

Thanks a bunch if someone can help;)

---

### Post by muffinhead on 2006-07-03
Bump, in one of my last posts, I posted the error I get, when booting into recovery mode, with my Geforce FX 5500, enabled in the bios.

If anyone can help me solve this problem, I'd be so thankful, Thank You;).

---

### Post by muffinhead on 2006-07-04
**Bump! **Please help me solve this problem, Thank You;)

---

### Post by muffinhead on 2006-07-04
**Bump.**

I've bumped this thread countless times, hoping someone would reply, and help me solve my problem.

I still haven't got any real help or solutions, neither any suggestions, that could quite possibly help me solve my problem, and my thread constantly keep getting bumped to the next pages over, from this one.

If someone can take a couple to a few minutes to help me out, that would be great! I'd be so thankful:D.

If someone can take a few minutes to help me, get this sorted and taken care of, so I can use ubuntu, that would be excellent, Thank You;)

---

### Post by SIMPLIFYER on 2006-07-05
In your /etc/modprobe.d/blacklist, put this:

blacklist intel_agp
blacklist agpgart

instead of:

Intel_agp
agpgart
(that was for breezy)

---

### Post by pwp on 2006-07-05
I had this problem and found a solution ... at least for me (so far).

I have a laptop (Thinkpad) with an IBM PCMCIA Token Ring card. This Token Ring card has no connection (i.e. no cable plugging it in to the network). I found by removing the Token Ring card from my laptop - the problem goes away.

This seems to be a new problem with  2.6.15-25-386 ...  2.6.15-23-386 does not have the problem.

This fix seems to work with both "quiet splash" on and off.

---

### Post by muffinhead on 2006-07-05
[quote=SIMPLIFYER]In your /etc/modprobe.d/blacklist, put this:

blacklist intel_agp
blacklist agpgart

instead of:

Intel_agp
agpgart
(that was for breezy)[/quote]

Thank you very much for replying ;-) I really appreciate it. I really hate having to double, triple, or quadruple post, in order to bump my thread back to where it can be seen.

I'll try what you mentioned, and let you all know if it works, hopefully it will:D

---

### Post by muffinhead on 2006-07-06
[quote=SIMPLIFYER]In your /etc/modprobe.d/blacklist, put this:

blacklist intel_agp
blacklist agpgart

instead of:

Intel_agp
agpgart
(that was for breezy)[/quote]

Thank you!:grin:, that worked perfectly, my problem is now solved;-). 

If I run into anmore problems I'll post back here, but for now it's working fine, Thank You:)

---

### Post by Grog140 on 2006-07-20
First of all, thanks for all the helpful information posted in the thread.

Blacklisting the Intel Extreme Graphics got me past the loading hardware drivers problem. But after I am past that there is an error loading the X server and leaves me in a terminal.

I beleive the problem is that there is no entry for the card I am trying to use in the xorg.conf file. There is only and entry for the Intel extreme as a section device. Not the Radeon 9200 SE.

Would setting up a Section Device for the Radeon card work? If so then how would I go about doing that?

EDIT: By the way, lspci puts out 

```
40:01:02.0 VGA compatable controler: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

40:01:02.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```

---

### Post by mlind on 2006-07-20
> **Grog140 said:**
> 

I beleive the problem is that there is no entry for the card I am trying to use in the xorg.conf file. There is only and entry for the Intel extreme as a section device. Not the Radeon 9200 SE.

Would setting up a Section Device for the Radeon card work? If so then how would I go about doing that?

EDIT: By the way, lspci puts out 

```
40:01:02.0 VGA compatable controler: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

40:01:02.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```

You should install proprietary ATI drivers, instructions on this article
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Grog140 on 2006-07-20
Thanks, I got X to start.

But doing glxinfo, fglrxinfo gives a whole lot of errors. But things still seem to work anyway. So thanks, I will just need to make sure I have 3d rendering.

---

