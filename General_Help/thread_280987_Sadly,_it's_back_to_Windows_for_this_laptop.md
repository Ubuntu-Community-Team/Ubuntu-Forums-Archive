---
title: "Sadly, it's back to Windows for this laptop"
date: 2006-10-20
forum: General Help
---

### Post by pentarinfosys on 2006-10-20
After two weeks of working with it, attempting to track down all the problems and updating components, I have been forced, grudgingly, to conclude that this laptop, a Gateway MX6453, just will not run properly under anything but Windows.

The problems revolve around the sound card and the onboard wireless. The sound is a SigmaTel 9250 chipset (also detects as SigmaTel 7346) that produces an error when modprobed. It uses the hda_intel driver but results in an **invalid dep_range_value** error. The latest version of alsa (1.0.13) failed to correct the issue, and I was unwilling to spend money on the various commercial sound subsystems for Linux. If I was going to continue to use Linux, I was facing having no sound until the proper drivers caught up. This isn't the fault of the developers; it's squarely on the hardware manufacturers who won't release appropriate information to allow a Linux driver to be openly created, and won't develop one themselves.

Same thing goes for the Broadcom 4311 that's installed. The kernel driver wouldn't load (of course), and even the most current version of ndiswrapper failed to correct the issue, resulting in ntoskrnl errors when attempting to load this. ALthough a regular D-Link wireless card worked immediately for this machine, it wasn't optimal, and seemed like a waste, given the presence of an internal wireless card. This wouldn't have been enough to drive me back to Windows, but in light of the non-functioning sound, it was an extra impetus to restore XP.

As a last step before taking that course, I tried to install Edgy, but the installation failed after I selected the timezone I was in. No errors, nothing in the log... it just stopped. I had no diagnostic information to offer.

Finally, there's the fact that this is a Turion 64x2 machine. I originally loaded the amd64 version of Ubuntu, but the large number of applications that wouldn't run under 64bit, or required that I rip out the 64bit versions and replace them with 32bit (Firefox, for example) if I wanted certain codecs and plugins to work caused me to reinstall the laptop with the i386 version of Ubuntu. That meant that any advantage I would have received at all from having a Turion machine was lost.

Taken altogether, and given the fact that I wanted a _wholly_ functional laptop means, regrettably, a trip back to Windows-land. I'll look at trying the live CDs in 6 or 8 months, and see if the situation has changed. I'm offering this thread, not sullenly denouncing Ubuntu in particular or Linux in general, but in order to provide anyone else who comes in here, looking for help with this particular model of Gateway. As of 20 Oct 2006, the hardware is apparently just too new and full of too many closed-source components to make running Linux on it an affair that might appeal to anyone but the most patient, persistent, and experienced.

I'll be back in a few months.

---

### Post by dbott67 on 2006-10-20
> the installation failed after I selected the timezone I was in

Interestingly enough, this happend to me also.  After a few failed attempts, I just left the timezone as is and it installed fine.

Just figured I'd add that to the mix in case any one else tries it & gets stuck.

At present, I'm back to running Dapper on both my home computers.  I've got a Dell 6400 with a Broadcom 4311 and I needed to install the latest version of ndiswrapper to get it going.

I created a HOWTO for issues that I had (SMP, WIFI, ATI & Beryl).  Steps 1-4 cover getting wifi working (for me, anyhow).


-Dave

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

---

### Post by ssalman on 2006-10-20
I'm sorry to hear that...

I have a Gateway M320 laptop that worked remarkably well with multiple distros, but I did research it before buying the laptop to make sure I don't run into too much trouble down the road.:D

> Finally, there's the fact that this is a Turion 64x2 machine. I originally loaded the amd64 version of Ubuntu, but the large number of applications that wouldn't run under 64bit, or required that I rip out the 64bit versions and replace them with 32bit (Firefox, for example) if I wanted certain codecs and plugins to work caused me to reinstall the laptop with the i386 version of Ubuntu. That meant that any advantage I would have received at all from having a Turion machine was lost.Unless you are running Win 64-bit edition you are not using that either under windows, and even if you did use 64-bit windows, almost all your applications will be running in 32-bit mode... So I wouldn't be so hard on 64-bit linux as I think it is one step ahead on windows in that area, as I view it as a cutting edge product and early adaptors pay the price :(. 

The rest of your troubles seem to be valid issues with the current status of proprietary drivers, I don’t mean to flam you, but I think you voted with your money in the wrong box!! Next time Gateway designs a laptop they will lookup the previous trends and your purchase will be one of the statistical points pointing against Linux. Again not flaming :)

I hope your troubles will disapear with later versions of linux, and we will see more of you around here.:)

---

### Post by AlReece45 on 2006-10-20
> **pentarinfosys said:**
> Same thing goes for the Broadcom 4311 that's installed. The kernel driver wouldn't load (of course), and even the most current version of ndiswrapper failed to correct the issue, resulting in ntoskrnl errors when attempting to load this.

Works for me, of course I'm on edgy. Perhaps instead of trying to install edgy directly, you could upgrade from dapper (you don't have to start from CD to do this).

---

### Post by dbott67 on 2006-10-20
> **AlReece45 said:**
> Works for me, of course I'm on edgy...

This may be an issue with 32-bit vs. 64-bit.  I'm using i386 version with 686-SMP kernel and all is well, however, the AMD/64-bit version may not work properly.

-Dave

---

### Post by alecjw on 2006-10-20
That happened to me - but with edgy knot 3 instead. I did the text-based install instead.

---

### Post by Saubazi on 2006-10-20
I consciously selected hardware that I knew I could get to run under 64bit linux, for example atheros based wireless adapter and so on. You can guess my surprise when I then bought a 64-windows and all the netgear in combination with VIA chipset had to offer was blue screen. Most surprising was the trouble I went through to find drivers for my ASUS motherboard - can you believe that? Motherboard for 64-bit AMD and it does not have 64bit windows drivers? It was a hell to pay to get even installation on SATA. Afterwards I finally got my legally bought brand new win XP 64-bit activated and after installing firewall (one of the very few that work with 64bit) I installed some security update and started seeing blue. I have never had such problems with windows so I can say only one thing 64-bit Windows is POS. I had to format and then I installed it on an IDE drive - new trial same conflict with security updates + I could not activate, M$ site said that the code is used. Great - I threw to box to the shelf and promised never to take it out again - now I have somewhere in the corner of my harddrive windows 2000 for games and rest is 64-bit Ubuntu and I am convinced that if there is something that reasonably works with 64bit it is linux, period. Sure I am still finding my way around and it takes usually one or two days of searching but I usually find a solution. Sure I like Windows not as an OS but for the really well made 3rd party software that is what makes it so good in the end but you can forget about 64bit Windows...maybe Vista - I just dare not imagine what kind of piratchaseparanoia they come up to irritate the hell out of legal users with that one and as long as the games run under 2000 I am not going to find out...

---

### Post by Kleber on 2006-11-20
Hi Everyone

I've the same brand Gateway MX6453 laptop. I've installed the Ubuntu 6.10.

The Ubuntu 6.10 32-bits works fine over Turion 64x2.
I just have problem with sound so far.

I read some threads like this where users have the some problem.

Gateway Laptop, no sound
[http://ubuntuforums.org/showthread.p...ghlight=MX6453](http://ubuntuforums.org/showthread.p...ghlight=MX6453)

No sound: SigmaTel 9250
[http://ubuntuforums.org/showthread.php?p=1786184#post1786184](http://ubuntuforums.org/showthread.php?p=1786184#post1786184)

I hope someone can help us.

Best regards,
Kleber Rodrigo de Carvalho

---

### Post by Cefka on 2006-12-30
I too recently got an MX6453 and had problems with sound when I tried dual-booting between XP Media Center and Kubuntu ("Dapper Drake").  I've been googling the hell out of the problem and just recently came across something on gmane that might be of interest.  Someone's working on an ALSA patch for the Sigmatel 9250 in the newsgroup gmane.linux.alsa.devel.  The patch's filename indicates that it's for the mx6454 model.  However, I think it's safe to assume that it'd work on the 6453 if it works on the 6454 as they both have the 9250.

[Sigmatel STAC9250 Test Patch]("http://thread.gmane.org/gmane.linux.alsa.devel/42922/focus=42922")

[A semi-related bug might provide a hint as to what's wrong, but not likely.]("http://thread.gmane.org/gmane.linux.alsa.devel/43342/focus=43382")

The patch is in version 7 presently and still doesn't work, but at least there's a faint glimmer of hope.  There's at least one developer (and a bunch of testers) hard at work on this.  I'm keeping my fingers crossed.

-Cefka

---

### Post by ardvark71 on 2006-12-30
> **ssalman said:**
> 
I hope your troubles will disapear with later versions of linux, and we will see more of you around here.:)

Usually they do after one or two releases. Perhaps Feisty, when released, might take care of pentarinfosys's problems.

Best Regards...

---

### Post by Kleber on 2007-07-03
I needed to set up a Gateway MX6453 laptop (Ubuntu 7.04) , because they (wireless card and sound card) were not working.
I followed your clue and the wireless card and sound card are working fine now.

Thanks so much.

Regards,
Kleber Rodrigo de Carvalho

---

### Post by Truefire on 2008-03-15
Gutsy Gibbon works great.

Use the alternate install cd,
and when you get done,

sudo apt-get install xserver-xgl

For graphics support.

Wireless is easy now.

---

