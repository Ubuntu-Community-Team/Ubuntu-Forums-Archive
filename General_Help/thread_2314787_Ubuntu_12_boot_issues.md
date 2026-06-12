---
title: "Ubuntu 12 boot issues"
date: 2016-02-23
forum: General Help
---

### Post by silas3 on 2016-02-23
First things first. I got an old Win XP 32 bit computer that had been converted to ubuntu 12.04 or 12.10, I honestly don't remember which. I'm not actually sure if it was XP 32 bit, but considering it's age and overall performance, it isn't a bad assumption. Anyway, I did a stupid, boneheaded idiot mistake of running boot repair 64 bit on the computer. I didn't even have I problem, I just felt like doing it. Again, boneheaded mistake, never fix something unless it's broken and never, ever try to install anything as important as a 64 bit boot manager, or anything else 64 bit, on a 32 bit system.

Anyway, whenever I boot up now, it gives me an error in typical white text black screen saying "Error booting" or something along those lines (I'll double check). If I click a button it just prints the same text under it again. Realizing the stupidity of what I'd done, I burned the 32 bit version of boot repair on a disk, and popped it in. Bootloader successfully installed etc. but same issue at startup again. I tried the grub doctor tool in pmagic 2013 (the last available version according to majorgeeks), and had it set to run my linux partition at default and installed on sda, my main partition. No luck. Using one of parted magic's grub tools without the graphical display, I successfully managed to boot into my main ubuntu OS, but that was using the disk, and not the main hard drive. Any ideas what I can do? If you need any more information or clarifications, I will be more than happy to provide. Thank you!

---

### Post by Bucky Ball on 2016-02-23
If you ran a 64bit program on the machine it is a 64bit machine. Boot Repair 64bit version wouldn't have booted if the machine was 32bit.

Secondly, do you know which release you are using yet? 12.04 LTS is supported until 2017, 12.10 is no longer supported. Big difference. If the former, worth pursuing a fix. If the latter, we don't provide support for it, but we can help you get to a supported release.

If you have no valuable data on this machine, I'd think about installing 14.04 LTS and move on. If you do have valuable data, you can back up to an external device using the install media then install.

(PS: If you provide the make and model of your machine we may be able to help, but, just to confirm, if you create install media of the Ubuntu 64bit version, will it boot on your machine? If so, you have a 64bit machine, use a 64bit OS.)

---

### Post by silas3 on 2016-02-23
Fast help! I can still boot into the thing, albeit very slowly, so I'll check the OS out. And as for the model of the computer, it is a dell dimension 5100. And if the problem isn't running 64 bit on a 32 bit, than what could it have done to break the startup?

---

### Post by Bucky Ball on 2016-02-23
Using an EOL release possibly? Not sure yet. Let's keep digging ... :-k

[Is it this]("http://www.cnet.com/products/dell-dimension-5100-pentium-4-3-4ghz-256mb-ram-80gb-hdd-xp-home/specs/")? If so, 32bit and amazed you got Ubuntu running on it at all if it only has 256mb of RAM. Have you installed more (can take 4Gb).

You really aren't going to get a lot from that machine and a new Ubuntu won't run well on that processor, although you could try, and certainly won't run on 256mb RAM.

Try Lubuntu or Xubuntu 14.04 LTS, but again, with that much RAM, don't love your chances.

Boot from Boot Repair (a 32bit version) and you get the option to create a 'bootinfo'. Do that, don't run a repair, just create the bootinfo, and post the link here, please.

---

### Post by silas3 on 2016-02-23
Ok, according to ubuntu itself, it is 12.04 LTS (woop!), and the OS type is 32 bit. The memory is 740.1 MiB and the disk space is 77.7 GB, so considering the hardware, I'd say it probably would be an old 32 bit XP, but I'm not too experienced with that so I'm not sure. That would of course answer why the 64 bit boot repair broke my boot. Of course there's the question of why it let it. And so we're 100% on the same page, I'm running the cd/dvd at BIOS startup I think as a livecd. Does any of that help?

---

### Post by Bucky Ball on 2016-02-23
Right. Try the 32bit Boot Repair and see if that gives any joy. But first, give us the bootinfo (info edited into my last post, you may have missed). 

You can boot from Ubuntu install media and [install Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") in a 'live' session there (choose 'Try Ubuntu'). Post the link to the bootinfo it spits out back here, please.

As I say, 12.04 LTS would be struggling on that (looks like you have 1Gb of RAM with some being used for graphics) and moving up, you would need to install Lubuntu or Xubuntu. A new Ubuntu would give a fairly unsatisfactory computing experience on those specs, if it runs.

---

### Post by silas3 on 2016-02-23
Ok, I already did do the 32bit repair one on it's own separate disk, and it didn't work. And for boot info, I'll do that but I just discovered a plot twist. According to the securable program for window (ran on wine) [https://www.grc.com/securable.htm](https://www.grc.com/securable.htm) it told me I have a maximum bit length of 64, so the guy who installed ubuntu undershot it! Which is good but brings us spinning back into the other direction, why the heck did boot repair break my thing? I'm going to run the boot repair again on the info mode, I'll post the link ASAP. And during the previous "repairs" I took note of the urls it gave me, so here they are while I generate the other one. 

From "repair" that broke my startup: pastebin.ubuntu.com/15184021/
From "repair" that didn't seem to do anything: pastebin.ubuntu.com/15184239/

---

### Post by silas3 on 2016-02-23
And yes that is my computer but it has been upgraded (some) according to details it has 740.1 MiB memory, Intel® Pentium(R) 4 CPU 3.00GHz × 2 processor, Gallium 0.4 on ATI RV370 Graphics, 32 bit OS (but 64 bit compatible apparently) and 77.7 GB Disk space. And the pastebin I got from running the repairinfo thing is pastebin.ubuntu.com/15184972/

---

### Post by silas3 on 2016-02-23
It has an updated processor apparently if it's 64 bit compatible, pretty sure it has more ram and I'm pretty sure the graphics have been updated because if I put the monitor in the plug at the normal place in the back, it says something like "Your hardware has been upgraded, so please plug the monitor in to the updated slot at the bottom". I'm obviously paraphrasing :p. So we are not dealing with an out-of-the-box computer here. Of course with all these upgrades, it ranks at best as a potentially decent speed windows 7. EDIT: For the record I might add that ubuntu 12.04 is running pretty smoothly on here, there is practically no lag with having chrome and settings open, which is more than I can say about an old XP that I own.

---

### Post by Bucky Ball on 2016-02-23
Yep, must have more RAM in it.

Intel® Pentium(R) 4 CPU 3.00GHz × 2 processor

Without the exact model, hard to tell which this is. Don't be confused by the '2 processor' part. The P4s were mostly hyperthreading processors, which is not 64bit but gives the impression it is, while a handful were authentic 64bit dual-core processors. I just retired a machine with exactly the same processor you describe (at least with those details). It was a 32bit hyper-threading 3Ghz P4 and appeared exactly as you describe yours.

For a start, open a terminal and

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors.

---

### Post by silas3 on 2016-02-23
So do you think it could run say Xubuntu 14.04 LTS 64 bit fine, or better not? And I feel really, really, really stupid right now. I was looking through my own log and I saw that thing that said "make sure your primary sda partition is set to boot up first in BIOS". It wasn't. For some reason beyond me, it was set USB device. Set my hard drive to be first, and BAM! it worked. Thanks for your help, even though you didn't directly fix it :p. Anyway while we're here, could I run Xubuntu 14 64bit, or would that be a stretch?

---

### Post by silas3 on 2016-02-23
So far I finished up to the update one and here are things that look like they might be errors: 

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages)

---

### Post by Bucky Ball on 2016-02-23
Not a stretch at all. Xubuntu is my preference and lighter than Ubuntu. It would be a better choice. Lubuntu is even lighter again, but don't like the LXDE desktop environment personally. :)

Recommend Xubuntu 14.04 (PS: there is also Xubuntu-core, a very light version with not much included, but easy to add what you want using the package manager, Synaptics in Xubuntu rather than Software Centre). Xubuntu-core started from 15.10 though. You can install a 14.04 version, but it is a little tricky.

---

### Post by silas3 on 2016-02-23
I'll go with regular Xubuntu 14.04, thanks for the tip though! I am still running the other commands though, but I'm 79% done with the upgrade one. I had a problem with another one of my computers (an emachine) that did not want to run ubunutu, and it gave a black screen at startup. Someone on this forum told me about Xubuntu, which works like a charm :) EDIT: Got through the upgrade command no errors. Now for the last one!

---

### Post by silas3 on 2016-02-23
And all done! No errors except the one I mentioned! I'm good to go for Xubuntu 14.04 than. Thanks for your help and one last question. Should I install the 64 bit version or the 32 bit?

---

### Post by Bucky Ball on 2016-02-24
Good news and no problems. Run this:

```
lscpu
```

In the output, check the second line. If it looks like this, you are running a 64bit processor and good to go with 64bit Xubuntu. If not, 32bit it is. 

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
```

Once installed, whichever you go for, remember to do a full update (don't bother doing that or installing third-party software during install as it can sometimes cause issues and both can be done once installed). 

Please see the first link in my signature to mark the thread as solved as your initial problem is fixed. This will not close the thread to further discussion, just helps others. :)

---

### Post by silas3 on 2016-02-24
OK, I ran it and it says 
Architecture:          i686CPU op-mode(s):        32-bit, 64-bit

That means I can go 64 bit, I take it?
EDIT: I also ran the livecd for Xubuntu 14.04 64 bit, and except a slow startup (after all, it is from a cd) it works smoothly! Should I install it as soon as I move my files?

---

### Post by Bucky Ball on 2016-02-24
Yes. :D

---

### Post by silas3 on 2016-02-25
Yes! Thank you for your help! I really apprectiate it. :D

---

