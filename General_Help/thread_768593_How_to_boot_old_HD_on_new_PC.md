---
title: "How to boot old HD on new PC?"
date: 2008-04-26
forum: General Help
---

### Post by wbsorsby on 2008-04-26
Motherboard failed during a thunderstorm the other day, so I'm getting a new PC. I'd like to boot from the old HD initially. How tough is that gonna be?

Old PC was single core Pentium (2.4 GHz) with N-Videa AGP graphics card. Assuming I get a dual-core with PCI-E (or whatever), what obstacles am I gonna run into?

Thanks in advance,
Bill

---

### Post by ryanhaigh on 2008-04-27
If you stick to nvidia for graphics you should have minimal issues, your partitions UUIDs should remain the same so you shouldn't have to worry about editing grub and fstab for that (providing this info incase they for some reason do change you have a starting point for solving that issue)

You may need to reconfigure your networking if you don't use network manager as the network card on the board with have a new mac address so will likely be eth1 instead of eth0. 

Same deal with sound, if you have done anything specific to your old board/chipset it MAY have issues.

I have transferred a system to new hardware a few times and the only real issue I had was video as I went from ati to nvidia and the ati driver was kind enough to leave files all over the place when removed. That and getting used to typing eth1 instead of eth0 but most people probably just use network manager and never worry about such things.

---

### Post by ghost_ryder35 on 2008-04-27
might run into a lot of hardware configuration issues as most things will be diffrent. like ryan said video is going to be a problem, more than likley you will not be able to boot into x and only get a terminal. will have to run
```

**sudo dpkg-reconfigure xserver-xorg** 

```
to reconfigure the card, some other things may be necessary.
 
What I recommend is to mount the hard drive as a secondary slave in the new box, boot off of the live cd, install hardy and then you could mount (during the install) your /home directory on your old hard drive that way you would still have all your old files, configurations and programs, and save your self of trying to boot a system that will have multiple problems. Just my $.02

---

