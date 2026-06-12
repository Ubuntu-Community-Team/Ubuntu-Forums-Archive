---
title: "netbook won't boot Ubuntu from flash drive"
date: 2015-04-20
forum: General Help
---

### Post by Don_Evans on 2015-04-20
First time poster and new Ubuntu user. Have been helping a family member figure out what to do with her HP Netbook Mini running XP. I have some personal experience with building and repairing systems. First, I recommeded not using XP! :mad: The Netbook has 80 GB HDD and an Intel Atom processor with with one stick of DDR2 memory. Yeah, fairly old and outdated. i found malware on it and fixed it with MBAM pro. Runs fairly quickly after tweaking her progs and uninstalling needless apps, etc. Probably would have trouble running W7, which she doesn't want to buy for $93 from the Egg. She uses OpenOffice on it, so I suggested installing an open BSD OS. After research, I installed Ubuntu 64bit to a thumb drive using UUI app and have been using it on my HP Probook 4530s without problem. Very quick OS. Still learning to use it, but can do the basics like browsing, emailing, and writing documents. 

For her Netbook, i installed the 32 bit version of the 14.04.2 LTS build with UUI on another thumb drive and booted up after changing the boot order. It recognized Ubuntu, and I selected "Use without installing,"
It just hangs on black screen, so I wonder if the Netbook has the necessary requirements for running it. The HDD has 55GB available. Does it just take a while? Any ideas? 

TIA,

Don

---

### Post by kerry_s on 2015-04-20
i have the hp mini 210-1010nr, it only has 1gb stock, i've got a 2gb stick on order to max it out.

but yeah, your going to have to go with a low resource version, lubuntu or xubuntu, something with less 3d.
i use elementary os on mine, it's usable but i could really use the upgrades i got on order. lol

---

### Post by RobGoss on 2015-04-20
Sometimes depending on the machine especially something that's running Windows xp it might not have all the requirements

On the other hand, I also have a Netbook mini with 1.5 of ram and was also running Windows xp. its now running Linux mint 17.1 like a pro.

I would say try different distribution to see which ones perform the best. There's a few lighter versions of Ubuntu as well.

Do you know how much ram is on that Netbook?

---

### Post by kerry_s on 2015-04-20
> **robert159 said:**
> Sometimes depending on the machine especially something that's running Windows xp it might not have all the requirements

On the other hand, I also have a Netbook mini with 1.5 of ram and was also running Windows xp. its now running Linux mint 17.1 like a pro.

I would say try different distribution to see which ones perform the best. There's a few lighter versions of Ubuntu as well.

Do you know how much ram is on that Netbook?

1.5gb ram ? so you have 2gb & the system uses 512mb ? i ordered 2gb, i hope i don't lose that much. lol

---

### Post by Don_Evans on 2015-04-20
I ran a system tool and can't figure out if it can handle a larger RAM stick. How much did it cost?

---

### Post by Don_Evans on 2015-04-20
1 GB ram stick.

---

### Post by Don_Evans on 2015-04-20
Thanks for the feedback guys.

---

### Post by kerry_s on 2015-04-20
> **Don_Evans said:**
> I ran a system tool and can't figure out if it can handle a larger RAM stick. How much did it cost?

[http://www.amazon.com/gp/product/B002TWXLRG/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B002TWXLRG/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)

my system is 2gb max, it's so worth the performance gain from more ram. i looked inside there's only 1 slot.
i'm also using a sd card sata adapter, which uses 2 sd cards in raid 0, i currently have 2 missed matched sd cards in there, so i ordered another so i can have 2 90mb/s sd cards, i may order an ssd later on if i can find a good price. it makes a world of difference using a drive with no moving parts.

---

### Post by mattharris4 on 2015-04-22
Ubuntu will not run on 1GB RAM -- at least usably.  If it will run at all it would be slow as molasses on a -40 degree Nunavut day.  In my experience 2GB RAM is pushing the envelope using Ubuntu.  If the computer cannot be maxed out (for 32 bit, which this netbook likely is) at 3.2GB RAM (you would install two 2GB sticks and the computer would recognize 3.2GB of it) you definitely need to use a lighter OS.  

For most purposes Lubuntu will run fine (assuming it will install and it has the correct drivers for this ancient computer) but RAM hog sites such as SFGate will bog down a bit as it will require swap to load (SF Gate with a few tabs open will run about 1.2GB of RAM using Lubuntu).  You could try Puppy Linux, if the drivers are all there it will probably work great in this computer (it certainly won't require a full GB of RAM to run even with Firefox) but if a driver isn't there or of the installer won't run for some reason the support available is minimal outside of YouTube videos and the FAQ and instructions on their website (granted, I am used to Canonical level support).  Also, the install process is more complicated, search for "Puppy Linux" on YouTube and watch a few installs before attempting one yourself.

---

### Post by kurt18947 on 2015-04-22
I agree with a 'lighter' O.S. I have an HP Mini w/ 1 GB. RAM. You must use a 32 bit O.S. obviously. I've had Mint running usably. I just downloaded the beta of Ubuntu Mate 15.04. I'm running it on a notebook with 3 GB. RAM but the install uses around 300 MB. This seems like a nice choice for modest machines. I did not designate a swap partition but would if I had < 2 GB.  I've purchased used PC2-DDR5300 from Ebay with good success. I make sure I can return it if after installing it, memtest shows problems.

Re installing, I sometimes find retro is good. I bought a Samsung USB DVD/rw a few years ago. I have had problems booting and installing from USB drives, especially on older machines built when booting from a flash drive was new. I don't recall ever having a problem booting or installing from a CD/DVD. It's slower but reliable in my experience.

---

### Post by Vladlenin5000 on 2015-04-22
I have to strongly disagree and I have the experience to back it up: **Standard Ubuntu (with Unity) runs quite well in similar netbooks provided you don't open too many apps at the some time, obviously (1GB is really short)**. Of course, lighter desktops are snappier, but not by much, really.

You may have video issues with some older Atom based netbooks depending on the integrated Intel graphics more than anything else. Usually the open-source Intel Graphics drivers install uneventfully and just work. However, there are a few made for Atoms by a third party with closed source drivers. Those chips have been proven quite problematic in Linux, time and time again. I'm afraid there's no good solution for it and it'll never be. 

Thing worth trying:

***nomodeset***  - When you're at the Try Ubuntu menu press F6 and select nomodeset. 
Although usually for nvidia I had to use it once in a 15.6" ACER laptop with Intel Graphics (can't remember which, circa 2009/2010) with the same symptom and then installed the Intel drivers.

This option should at least give you generic video but with wrong resolution. At least you should be able to open a terminal a check a few things about the system.
Posting the complete model here - or better yet search for it in forum - is also a good idea.

---

### Post by kerry_s on 2015-04-22
> **kurt18947 said:**
> I agree with a 'lighter' O.S. I have an HP Mini w/ 1 GB. RAM. You must use a 32 bit O.S. obviously. I've had Mint running usably. I just downloaded the beta of Ubuntu Mate 15.04. I'm running it on a notebook with 3 GB. RAM but the install uses around 300 MB. This seems like a nice choice for modest machines. I did not designate a swap partition but would if I had < 2 GB.  I've purchased used PC2-DDR5300 from Ebay with good success. I make sure I can return it if after installing it, memtest shows problems.

Re installing, I sometimes find retro is good. I bought a Samsung USB DVD/rw a few years ago. I have had problems booting and installing from USB drives, especially on older machines built when booting from a flash drive was new. I don't recall ever having a problem booting or installing from a CD/DVD. It's slower but reliable in my experience.

why must you use a 32bit os ? why not take advantage of 64bit multi-threading if your cpu supports it ? sure 64bit uses a bit more memory, but you gain performance, better use of the system resources.

i been playing around with the lighter stuff, so far i prefer xubuntu for my 1gb, works with no hiccups. just for kicks i tried gnome the other day, all kinds of issues, the main being the ui on my 10" screen.

---

### Post by kurt18947 on 2015-04-22
> **kerry_s said:**
> why must you use a 32bit os ? why not take advantage of 64bit multi-threading if your cpu supports it ? sure 64bit uses a bit more memory, but you gain performance, better use of the system resources.

i been playing around with the lighter stuff, so far i prefer xubuntu for my 1gb, works with no hiccups. just for kicks i tried gnome the other day, all kinds of issues, the main being the ui on my 10" screen.

I assumed most of not all Atom powered netbooks are 32 bit processors. Am I incorrect in that? As a result of this thread I started the HP 1000 Mini today, first time in months. I inserted a 15.04 Ubuntu Mate flash drive that I created a couple days ago. I was told in no uncertain terms that a 64 bit OS would not work on the HP Mini:razz:. I then downloaded and created the 32 bit version of Mate 15.04 Beta. It would start but hang after a few seconds. I then created a DVD from the same .iso. It behaved the same. I don't know if it was a bad download (didn't check the md5) or if that version and that machine don't quite get along. I didn't take time to play with it - do nomodeset, that sort of thing. It could well be a video issue based on where in the boot process it was hanging. Xubuntu does work well and with Firefox open was still only using 220 MB. of RAM and no swap. This machine had XP on it when I got it and what a DOG! No wonder Netbooks never really caught on.

Edit: I took time to boot Ubuntu-Mate 15.04 beta 2 using 'nomodeset'. It did boot to a usable live install. When I tried to install it, the installer window was larger than the visible screen so the buttons in the lower right hand corner were not visible. I'll experiment with -- vga=788 or similar and see how that works.

---

### Post by kerry_s on 2015-04-22
most modern cpu's are 64bit capable. i've heard about some being locked to 32bit in the bios, mostly atom 270's. 
mine's a hp mini 210-1010nr, the problem i have the most is the 10" screen 1200x600 resolution, sometimes apps will be larger then the screen, for example i had that issue in gnome. elementary os was pretty good, but i had issues with screen flicker & double cursor, i'm guessing a intel vid driver bug.

anyways i'm using xubuntu 15.04 64bit, i set it up like elementary os.

---

### Post by kurt18947 on 2015-04-23
> **kerry_s said:**
> most modern cpu's are 64bit capable. i've heard about some being locked to 32bit in the bios, mostly atom 270's. 
mine's a hp mini 210-1010nr, the problem i have the most is the 10" screen 1200x600 resolution, sometimes apps will be larger then the screen, for example i had that issue in gnome. elementary os was pretty good, but i had issues with screen flicker & double cursor, i'm guessing a intel vid driver bug.

anyways i'm using xubuntu 15.04 64bit, i set it up like elementary os.

Intel/MS deliberately crippling a processor??!? Say it ain't so!!! :shock:










;)

---

