---
title: "new install new network need guru"
date: 2008-03-01
forum: General Help
---

### Post by crucial123 on 2008-03-01
Have just ordered the parts for a new pc.

have been using dual boot ubuntu and xp ..with the xp for gaming and the ubuntu for pretty much everything else.

My new machine is a Striker formula with a core 2 duo e8400, 8GB ddr2-1000, gigabit lan,
2 SATA hd's  (which I plan to run RAID 0), and 2 9800glx's (as soon as I can get my grubby meathooks on them)

My old machine is a celeron 2.4ghz platform with two ATA hd's and a gigabit lan card

My intention is to run the old machine as  ubuntu only.  To have it chugging away in the background as a p2p client, email client and the like.

My new machine will be running Vista 32 or 64 bit ( I bought the retail box so I can be flexible)  (don't start... I want Directx 10 and full SLI)

So I am considering a couple of options for installing OS's on the new machine.
The first is a triple boot configuration Vista, XP, Ubuntu.

The second is a VM player installation of Ubuntu and XP on top of the Vista host

The third is a Vista and XP installation on top of a Ubuntu host (but I believe this would restrict my Vista VM to 32 bit?)

The fourth is a combination of multiple boot and VM machines (which seems overly complicated and probably unnecessary.) 

I am mostly concerned with getting the best results while gaming on my new rig, I have no love for Redmond but at this point in time running a Microsoft OS natively seems to be the only option

I would still like to do most of my computing on Ubuntu, and the virtual machine seems like the way to go for this. Using Vista as the host OS seems the most hassle free solution as far as upgrades and security plugs and Microsoft licensing snafu's would be more streamlined. Not to mention overclocking and the like for gaming.

I am a little confused on how to best utilize my old machine. Do I run it as a headless server (Ubuntu) even though it will have much less hard drive capacity than my new rig? Do I just run it as a network client? 

I am fairly competent in both windoz and linux. No IT wizzard, but I usually resolve problems by reading forums and being bull headed ( I got compiz working with an agp ATI 1550 so you know that I can be bull headed)

I am just trying to really get my head wrapped around the structure of my little network BEFORE I start installing anything.

So to encapsulate this as simply as I can
I own Vista retail
I own XP OEM
I want to use Ubuntu for the majority of my computing
I want to run games natively on Vista (or possibly XP)
I want to use my old box as a downloading platform
I would like the most streamlined setup possible

I am open to Ideas 
bring em on

Thanks.

---

### Post by louieb on 2008-03-01
Have you thought about using a KVM switch to share keyboard,mouse, and display. Then its Scroll-Lock,Scroll-Lock some #. to switch from one machine to the other. 

Get a router and network them together to share data and internet. That what I've done for a few years now. Really like it.

---

### Post by fjgaude on 2008-03-01
Yes, Louieb has us pointed in the right direction. A LAN, fast gigabit router, connects the two machines and a KVM switch handle the keyboard, monitor and mouse change over from one computer to the other.

I've used such a setup, with my laptop and another computer, on the LAN, and that **switch** for many years. I do use two monitors, so I don't actually switch monitors, because none are good enough to eliminate blur, and none are digital. At least not the last time I looked.

That E8400 is some overclocker. Notice my signature. I do use other than stock fan, a Xigmateck DHT S-1283 on a Gigabyte P35-DS4 motherboard.

Let us know if you want any more suggestions.

---

### Post by crucial123 on 2008-03-01
thanks fellas

I was looking at [http://synergy2.sourceforge.net](http://synergy2.sourceforge.net) and this seems like a fairly elegant solution to keyboard and mouse switching.

There are dvi kvm's but they are pricey, I could buy a flat panel monitor for the same outlay.  Just call me Mr Wallofmonitors  42" viewsonic 1080p, 22" samsung widescreen, and a couple of 19" crt's ( I would rather pay $15 bucks at sally ann for a 19" crt than $250 for a flat panel to use for command line or text) 

I take it that I am on the right track with my installation plans, as both you guys came up with ways to make it more complicated..

Thanks

---

### Post by fjgaude on 2008-03-01
Okay, let us know if synergy works out... I've had my I/O Gear KVM switch for years now and it works just fine.

I trust synergy works with any video board that might be in your computers. Seems like it should work with any X11 system.

---

