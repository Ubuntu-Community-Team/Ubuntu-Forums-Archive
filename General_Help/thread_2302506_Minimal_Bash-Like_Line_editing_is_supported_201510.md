---
title: "Minimal Bash-Like Line editing is supported 20151010 (Install to USB)"
date: 2015-11-10
forum: General Help
---

### Post by benjaminsinger1974 on 2015-11-10
Yes I have been surfing the fourms for viable solutions, and nothing works yet.  Here is what I did: Created Mint cinnimon live USB and from that USB installed Mint on another 32 G USB (4 partitions and MD5 for ISO checked out). Turned off computer after install, removed both USB's, proceeded to boot back into Ubuntu 12.04 and recieved the "Minimal Bash-Like Line editing...." screen.  I have tried a few different suggestions from the online communities, I have tried drinking, I have even tried blaming various members of my household. Nothing seems to work. so before I FUBAR my system I was looking for any assistance here. heres the lowdown: HARDWARE: MB Sabertooth 990 FX AM3+ Processor: AMD FX 8350 16 G ram 1833 mhz Storage: 120G SSD Samsung EVO (for / and Boot) 3 TB storage drive.  SOFTWARE: Ubuntu 12.04 (primary booting OS)  Vitural box runs on this machine with various Debian fork OS's, Windows 7 (incase I elect to have a bad day) and a failed attempt at Solaris 11.

More:  [http://paste.ubuntu.com/13223269/](http://paste.ubuntu.com/13223269/)

A thought... what if I chmod /BOOT and remove the windows junk.  Because when I enter my BIOS or UEFI's as it were I can select to boot from somthing new that starts with WD or somthing. Just worried I'll wreck somthing. suggestions please before I drink myself to death. Soory I am a bit of a noob with the whole *nix thing. I do however have some basic understanding of the CLI. I work as a professional ladder holder several hours a day so any respose time on my part may be slow. Sorry.

Thanks all in advance!

---

### Post by ian-weisser on 2015-11-13
You must understand the problem, so you can use the right tool to fix it.

For example, it's really clear from the link that you have GPT and EFI. See all those 'Warning!' messages?

Seems like you are trying to install Linux to dual-boot with windows - the hardest, most complex, and most error-prone way to use multiple OS. Are you doing so because you want the complexity? Or because you don't know the easier way?

Simply put, your problem is that the boot information EFI is looking for is in a different location from the boot information GRUB is looking for.
Reinstalling usually won't help - the installer will continue to put the GRUB information into the wrong location.
One simple fix is to know exactly which disk EFI wants boot information on, then unplug the other disk so the installer (or just the GRUB-repairer) has no incorrect choice.

---

### Post by benjaminsinger1974 on 2015-11-13
Thanks IAN for the new Paradigm):P I had been failing to install Grub to my /Boot partition on SDA. so once I was able to mount SDA1 I changed my working directory as in "cd /media/-bunch.of.numbers-" then a "sudo apt-get install grub" worked. I still have the windows boot files that I need to get rid of. However they do not show in the grub menu upon booting. So yeah what-u-said is gospel! I wasn’t trying to dual boot, no reason to with virtual box. For whatever darn reason mint wanted to install windows as a dual boot on SDA instead of flat out installing to USB only. I'm up and running, just have to get rid of the windows crap in my boot folder. Be doing some more learnin' real soon.  Thanks again IAN!

---

