---
title: "Error after 7.04 install: ata2.00 : failed to set xfermode(err:mask=0x4)"
date: 2007-04-19
forum: General Help
---

### Post by Raffo on 2007-04-19
I've just installed feisty 7.04 (final) and I've a too long boot. I pressed ctrl+alt+F1 to take note of the error. This is my error: "ata2.00 : failed to set xfermode(err:mask=0x4)"

I found that it could be a kernel error, but I'm not able to install a newer kernel, my system is up to date. 

My hardware: P4 2.4 GHz, 512 MB ram, nvidia FX 5200, 128MB.

---

### Post by Raffo on 2007-04-19
little up.

---

### Post by flyingbrass on 2007-04-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Welcome to the club.  The last kernel that worked for me was 2.6.20-13.  My CD drive is no longer recognized.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410)
[http://ubuntuforums.org/showthread.php?t=404894](http://ubuntuforums.org/showthread.php?t=404894)

---

### Post by Raffo on 2007-04-19
> **flyingbrass said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Welcome to the club.  The last kernel that worked for me was 2.6.20-13.  My CD drive is no longer recognized.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410)
[http://ubuntuforums.org/showthread.php?t=404894](http://ubuntuforums.org/showthread.php?t=404894)
Yes, same bug. I've a lite on cdrw, I can't read CDs and my devices are listed as sda.... I can't understand why feisty was released with a critical bug like this...

---

### Post by jimbob on 2007-04-19
I think this bug was fixed with kernel image-2.6.20-15-generic

If that is what you have try:
   apt-cache policy linux-image-2.6.20-15-generic
linux-image-2.6.20-15-generic:
  Installed: 2.6.20-15.27
  Candidate: 2.6.20-15.27
  Version table:
 *** 2.6.20-15.27 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
        100 /var/lib/dpkg/status

Make sure you have the 2-6.20-15-27 version installed.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by tritonge on 2007-04-19
What I'm using is 2.6.20-15-27 and I'm still experiencing this problem. If I disable CDRW in the BIOS, the kernel boots very fast. Otherwise, during the boot up, the message of "failed to set xfermode...." appears three time before it finally give up, but the CDRW is not recoganized after the kernel is up.

---

### Post by stbub on 2007-04-19
Well, I'm now posting this from feisty.

I did have the "failed to set xfermode" error.

To make a long story short, I reinstalled from cd, but this time after a COLD boot of the system (i.e. flip the switch on the power supply, not just the reset button).

For whatever reason, I didn't see any error.

My system is an ASUS P5W DH Deluxe with an Intel Core2 Duo, jmicron disabled, and 2 sata disk and 2 pata dvd, all on the intel controller.

Doesn't make much sense, but here you have it (for me anyways).

---

### Post by tritonge on 2007-04-19
I fixed the problem by add sr_mod to /etc/modules.

---

### Post by flyingbrass on 2007-04-19
A cold boot didn't help me.  Nor did adding sr_mod to /etc/modules.

I'm using a Lite-On CDRW.  Asus P4P800 motherboard (ICH5).

---

### Post by Raffo on 2007-04-20
This is my kernel:

linux-image-2.6.20-15-generic:
  Installed: 2.6.20-15.27
  Candidate: 2.6.20-15.27
  Version table:
 *** 2.6.20-15.27 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
        100 /var/lib/dpkg/status


The problem is still here.

---

### Post by hardyn on 2007-04-20
Yes... a few are still having trouble with is problem... it is only with certain SATA drive chipset combinaitons... im not sure what the plan is for this... 

All i can suggest, is unfortunately, hold on for a little while AND submit bug reports until you turn blue... with a kernel failure 5 days before release im a little suprised that they did not delay the release of edgy... i guess it was decided that it was an acceptable risk.

i am, however, told that this is a main trunk problem and is not ubuntu specific, but each of the distros is handling it a little different.

definately agreed, this is not a great way to kick off such a hyped release.

---

### Post by flyingbrass on 2007-04-20
From what I've read this is in general a Linux problem.  However, 2.6.20-13 still works for me, so I know 2.6.20 is capable of working.  I split  "blame" for this problem between:

1) The wacky Linux devs for their rough transition.  Linux is going downhill, IMO.

2) The Ubuntu folks who toyed with Feisty's kernel until way too late in the game, ultimately ignoring bug reports such as the one I linked earlier.  They knew -14 was screwed, and even posted a notice to that effect in the Feisty forum.  I'm a little miffed that they just slapped in the latest version of -15 and declared everything fixed.

Ubuntu always tinkers with some major things until the last minutes before release. Beta and RC stages mean nothing other than time markers until final.  I wish they'd revamp their development schedule  to include a lockdown period for real testing -- in other words time to test a real RC.

I've been using Ubuntu since Warty.  This is the first iteration I can't use.

---

### Post by Raffo on 2007-04-20
We are the real testers. This is not a good thing

---

### Post by tritonge on 2007-04-20
What I did is follows:

1) Boot from cdrom, run lsmod and record all modules loaded (my machine has no problem at all to boot from the live cd)

2) Boot from harddrive and compare the modules loaded.

What I found is that the boot from harddrive didn't load sr_mod. The next step I did was to modprobe sr_mod (I'm not sure if this step is importat) and add sr_mod to /etc/modules

BTW, the IDE chip is ICH4

---

### Post by Raffo on 2007-04-20
> **tritonge said:**
> What I did is follows:

1) Boot from cdrom, run lsmod and record all modules loaded (my machine has no problem at all to boot from the live cd)

2) Boot from harddrive and compare the modules loaded.

What I found is that the boot from harddrive didn't load sr_mod. The next step I did was to modprobe sr_mod (I'm not sure if this step is importat) and add sr_mod to /etc/modules

BTW, the IDE chip is ICH4
I was not able to find important differences. I added sr_mod to /etc/modules but nothing changed. Iìm still waiting for a fix.

---

### Post by hardyn on 2007-04-20
go visit the launch pad, you might be in  better postion if you are a little more vocal.  the devs cant fix problems that they don't know about.

---

### Post by Raffo on 2007-04-20
> **hardyn said:**
> go visit the launch pad, you might be in  better postion if you are a little more vocal.  the devs cant fix problems that they don't know about.
I've already posted on the launchpad.

---

### Post by kernelsandirs on 2007-04-22
Same issue here 7.04 using Asus P4800 Deluxe
Lite On 40x (don't recall exact model)

I'll try the sr_mod here in a sec.


update:
Nope sr_mod was of no help I do not have a working cdrom drive now :-(

---

### Post by kernelsandirs on 2007-04-22
Well I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

---

### Post by luxus on 2007-04-23
ok irqpoll helps..
now booting up running fine.. but i don't know what the option does ;D

---

### Post by Orbatos on 2007-04-23
> **kernelsandirs said:**
> Well I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

Hmm, as for luxus this worked, but the real question is why...

---

### Post by flyingbrass on 2007-04-23
Someone mentioned in another thread opening and closing the CD drive during boot.  It works for me.

---

### Post by Robin T Cox on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well done, kernelsandirs!! The 'irqpoll' works for me too. :KS

---

### Post by dresbo on 2007-04-24
irlpoll in the grub startup line worked for me too - this was the only thing I did to get it to work.

---

### Post by Ez-Toni on 2007-04-24
Hi everyone,
i'm reassured to see i'm not alone having this bug.

To add informations, i have a lite-On cdrw device and it's **not** in Sata.
I will try irqpoll solution tonight, hope this will work.

thanks and sorry for this frenchie's english ^^

---

### Post by Ez-Toni on 2007-04-24
Great ! it works for me too :KS

---

### Post by amosharper on 2007-04-24
> **kernelsandirs said:**
> Well I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

This did the trick for me. Loading time is normal now.

---

### Post by DarkStarAeon on 2007-05-03
That worked for my wifes computer! 

Thanks to vratnica  for pointing this thread out to me. :)

I noticed a few people said they had the ASUS P4P800 Deluxe, my wifes computer also has that motherboard, hmmm.

---

### Post by sprog on 2007-05-24
It fixed my slow startup too, I am sooo happy!   it is an older laptop: Acer Travelmate 521TE, 600MHz, 256MB, 5gb HDD.   I had to add "irqpoll" to the boot menu when I installed Edubunto 7.04 from CD, but for some reason the thought of having to add it to /boot/grub/men... after installation hadn't crossed my mind.   :-)

---

### Post by Eicca on 2007-09-07
[http://paste.servut.us/plain/zir](http://paste.servut.us/plain/zir)

There is the same error, if someone needs bug reports :) This is weird, because I was able to boot to Ubuntu for the first times after like 2-5 reboots, but now it wont work at all.. :/

Someone have told me about some irq things, but if those are not permanent fixes, then I think i am going to wait for just a new kernel.

---

### Post by Eicca on 2007-09-14
Sorry about the double post, but im really getting frustrated with this satans creation (windows), so does this error still exist in the 7.10?

---

### Post by gigaferz on 2007-09-14
finally a thread with the same issue ive been dealing for the last month...

I will try the workarounds tonite,,  my kernel is uptodate  (just did it yesterday hoping for a fix)

as far as I remember the "name " of my mobo  is gamila, it is an old hp  a518x.

*****************************************************

It works!!!!
**irqpoll  *

---

### Post by Eicca on 2007-09-15
How come when i add the irqpoll to the boot options, it still wont work? o__O

---

### Post by Eicca on 2007-09-18
Sorry for the double post and bump, but can someone help me? Please.

---

### Post by hatchek on 2007-09-28
Been having this problem myself. Set your CD ROMs to use Cable Select, not master/slave. When I did this, the boot lag ceased.

---

### Post by FrankVdb on 2007-10-13
I'm currently re-installing a home server with an Asus P4P800 SE motherboard and I'm having a lot of problems too. 

A lot of P4800 motherboards have died since they came on the market a couple of years ago. The ones made in Taiwan seem to be better quality than the ones made in China. A lot of the China-made P4P800's have died. 

I'm not sure but the problems mentioned here could also be hardware-related.

I've installed Ubuntu on an IDE drive but it is recognised as an sda drive. This is also the case for the slave drive on that same IDE cable.  

I have tried to connect IDE drives to the SATA connectors using an adapter but the mobo doesn't recognise it... 

Could be an SATA I or SATA II problem, I didn't know there is a difference...

I must also mention that I haven't tried to install another distro on that mobo yet and that my BIOS has never been flashed to a more recent version (currently version 1006).

---

