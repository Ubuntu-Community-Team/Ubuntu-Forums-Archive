---
title: "Boot is failing...."
date: 2008-02-29
forum: General Help
---

### Post by LookUpSeeBlu on 2008-02-29
Hi,

I installed Ubuntu (7.04) about three months back without a problem.  Then the hard drive on the laptop failed and I am starting fresh (7.10) on a new laptop (laptop is an IBM T60, a year old, on a shelf in the server room for the past 10 months).  I was able to install without a problem and then reinstalled all my apps from the Ubuntu tree.

This worked for about two days and now suddenly it will not boot.  It freezes up.  So I booted using the Recovery boot option in the grub menu.  

I have booted many times and sometimes it gets to here:

```

[       18.616000] APCI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21

```

Sometimes it gets to here:
```

[       18.616000] APCI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21

* Setting the system clock                                            [ OK ]
* Loading kernel modules...
* Loading manual drivers...
[        19.144000]  lp: driver loaded but no devices found
                                                                                      [ OK ]
* Activating swap...                                                      [ OK ]
* Checking root file system...
fsck 1.40.2 (12-Jul-2007)

```

Sometimes it gets one line further:
```

Filesystem seems mounted read-only.  Skipping journal replay.

```

What confused me the most, is when I tried to boot with the system ISO to try to use it to repair the filesystem, it wouldn't even boot the CD.

Any thoughts?  As the I.T. Director of my company, two laptops in a week is making me cringe....

Thanks.

Kevin

---

### Post by jeffus_il on 2008-02-29
Thoughts are easy, solutions hard...
Maybe there's a reason the machine was dumped on the shelf for 10 months?
Is the "system iso" the Ubuntu live cd?
I would try to boot with some other disk as well to rule out a hardware problem.

---

### Post by LookUpSeeBlu on 2008-02-29
The system was put on a shelf because the person using it left the company and we did not replace him/her.  The ISO is the Ubuntu Live CD.  

I think I have an older Gentoo Live CD laying around, I will try booting with that.

I hope it isn't a hardware problem.  Two laptops in a week and a month ago, another laptop got fried when it got "coffee'd" by a user.  We are a small shop and I can't be losing all these machines!

Thanks for your reply.

Kevin

---

### Post by LookUpSeeBlu on 2008-02-29
Okay...  I found a 7.04 livecd and tried to boot with that.   Now I am getting :

```

* Loading hardware drivers...
[       73.012000] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt
Error: -22
[       76.096000] intel_rng: FWH not detected
                                                                                    [ OK ]
* Loading kernel modules...
* Loading manual drivers...                                           [ OK ]
* Checking file system...
fsck 1.40-WHIP (14-Nov-2006)
                                                                                    [ OK ]
Mounting local filesystems...                                        [ OK ]
Activating swap file...                                                  [ OK ]
Configuring network interfaces...


```

When I rebooted again with the livecd, it stopped just after the FWH not detected line...  

I am guessing a hardware issue... does any of this clue in on WHAT it could be?

Thanks.

Kevin

---

### Post by nlong on 2008-02-29
It could be many different things.  I would check the memory first.  If it has any additional RAM installed, pop it out and run off the integrated stuff.  I've had similar problems due to bad RAM.

---

### Post by jeffus_il on 2008-02-29
Yes, one of the live cd boot options is a memory test, I wonder if that passes.

---

### Post by LookUpSeeBlu on 2008-02-29
Ok.  This is strange (meaning, I have never encountered it).  

This is an IBM T60.  The battery doesn't work at all (and I found out the other day that there is a 2nd recall on lenovo laptop batteries so I bet this is part of that).  I just run it plugged in.  

It has worked that way.  

Now, though, it doesn't boot with the battery in with a power cord plugged in, does boot without the batter in....

Odd, but I am up and running.  I have never seen a battery prevent a machine from starting...

Thanks for your help and support.

---

