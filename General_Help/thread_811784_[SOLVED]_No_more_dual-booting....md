---
title: "[SOLVED] No more dual-booting..."
date: 2008-05-29
forum: General Help
---

### Post by Powerman2442 on 2008-05-29
So after some time taking a "break" from Ubuntu 7.04 (for World of Warcraft) I finally decided to stop playing for my own personal reasons. A few days ago I decided to check out VirtualBox. After I found out what you could do with it I decided to try it with my old Ubuntu 7.04 LiveCD. Worked perfectly... even a bit faster than booting from a LiveCD and running the OS from the LiveCD.

After a few minutes of playing with VirtualBox I decided to check out other distributions. I went to distrowatch.com for ideas on what Linux versions to try. After a few days I have downloaded Damn Small Linux 4.4 RC1, Solaris 2008.05, PCLinuxOS 2007, and openSUSE 10.3 Gnome. 

Since trying all of them I no longer wish to dual-boot Ubuntu to Windows Vista anymore. I'd like to triple boot Windows Vista Home Premium, Ubuntu 8.04, and openSUSE 10.3 (soon to be 11). Is it possible to do this? What bootloader would be the easiest to use? Previously when I dual booted I used to Ubuntu bootloader and I know how to edit and change it. Haven't looked much into openSUSE yet but since trying it "I need it."

Have any of you used openSUSE? It seems like a fairly popular disto of Linux, but I was just curious. I personally like how it appears and operates, but I'd like to stick with Ubuntu. Which I currently only have one operateing system on this PC, because I was going to upgrade to 8.04 from 7.04. Should I upgrade or stick with my older version of Ubuntu?

Also I am currently running with an 120 GB HDD, 111 being available for use. How much do you think I should allocate to Ubuntu and openSUSE. My Windows Vista partition will be the first and main one because it will have all of the main software and games I run.

Any information is great

Thanks,
Powerman2442

---

### Post by Powerman2442 on 2008-05-29
Anyone have any feedback on this?

---

### Post by Pi rules on 2008-05-29
> **Powerman2442 said:**
> Since trying all of them I no longer wish to dual-boot Ubuntu to Windows Vista anymore. I'd like to triple boot Windows Vista Home Premium, Ubuntu 8.04, and openSUSE 10.3 (soon to be 11). Is it possible to do this? What bootloader would be the easiest to use? Previously when I dual booted I used to Ubuntu bootloader and I know how to edit and change it.

I would recommend using GRUB, which is probably what you have been using with Ubuntu.  bodhi.zazen wrote an excellent multi-boot guide [_here_](http://ubuntuforums.org/showthread.php?t=724817).

> **Powerman2442 said:**
> 
Have any of you used openSUSE?
Yes, I've tried most of the major distros out in VirtualBox and (previously) VMware and liked openSUSE (although I liked Ubuntu more).  I'm going to try openSUSE 11 very soon.

> **Powerman2442 said:**
> 
Which I currently only have one operateing system on this PC, because I was going to upgrade to 8.04 from 7.04. Should I upgrade or stick with my older version of Ubuntu?

I recommend upgrading to 8.04, which is a long-term support release (updates will continue until 2011 for the desktop OS).  It upgrades easily, but backup your important data before you upgrade and multiboot just in case.

> **Powerman2442 said:**
> 
How much do you think I should allocate to Ubuntu and openSUSE.
That is a tough question.  The multiboot article recommends having some sort of shared data partition and provides info on doing that.  You can use the same swap partition for openSUSE and Ubuntu in addition to the data partition if you decide to make one.  The exact amounts depend on how much space you have left and how many programs you are going to install in each OS.

---

### Post by Powerman2442 on 2008-05-30
Yeah I've personally never messed with a Windows bootloader and I have heard anyone who does usually has problems.

Yeah, I like openSUSE because of the interface. Similar to Windows, which is where I feel safe. I was just going to get rid of Ubuntu and use Vista and openSUSE, but I decided to try triple booting.

Okay, I download 8.04 last night.

Currently I have a 120 GB HDD, 111 GB available for use, and 59.5 GB free. I can free up 10.6 GBs by simply uninstalling Diablo 2 (1.83 GB) and World of Warcraft(8.77 GB). I am wondering how much I should allocate per OS. I did 24 GB for Ubuntu 7.04. And I used 4 GBs for the swap file. They said to make a swap "double" your ram. Is that even required? I mean I can understand why to use it if you had something like 256 MB of ram, but I have 2048 MBs. Windows doesn't even use close to 50% of my virtual memory (pretty much a swap file) so I doubt Linux (using less memory by default) would use all my 2 GBs of ram and then a 4 GB swap partition.

As for what I plan to do with each program. In the past I usually check out a lot of programs to see which ones I like. I try out some of the native games which are fairly fun time burners. I don't plan on having any huge games like I do on Vista, which is why Vista's partition will be by far the largest.

My plan was to do at least 22 GB per openSUSE and Ubuntu. Having 20 for storage and 2 GB for swap, but now know that you can share the swap I might make one partition 20 GB and the second 22 GB. I will have to look more into that though. As or being able to share the files in between, that isn't going to be a problem. I'm mainly using these for fun, nothing business related. So the chances of me needing something from the other OS are slim.

Thanks for the info and I will look into sharing the swap.

---

### Post by WRDN on 2008-05-30
Its perfectly possible to tri-boot the 3 OS'.
You will need to make a new partition for openSUSE- this should be the 4th primary partition- you can only have 4 primary partitions on a HDD without trouble.
You will then need to ensure both openSUSE and Ubuntu can use the same swap partition.
Finally, you should be able to edit the grub boot loader in Ubuntu (/boot/grub/menu.lst) to add the entry for openSUSE.

---

### Post by Powerman2442 on 2008-05-30
> **WRDN said:**
> Finally, you should be able to edit the grub boot loader in Ubuntu (/boot/grub/menu.lst) to add the entry for openSUSE.

Thanks I was just going to look up where the grub menu was. I've edited a few times before, but That was a few months ago.

---

