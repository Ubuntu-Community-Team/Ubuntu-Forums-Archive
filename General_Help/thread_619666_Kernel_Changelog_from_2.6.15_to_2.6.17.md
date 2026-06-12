---
title: "Kernel Changelog from 2.6.15 to 2.6.17"
date: 2007-11-21
forum: General Help
---

### Post by robmiracle on 2007-11-21
I've got a problem with my computer and I'm trying to track down some information.

I have an HP computer I picked up at best buy a couple of years ago.  It has a Pentium D 830 processor in it.   Any way, about a year ago, I was running Windows and it just stopped cold.   I could not boot from the hard drive nor could any variant of Windows 2000 or XP boot from CD.  It would always stop after the progress bar hit the end.    I was successfully able to boot Dapper on it, save the files and after realizing I would not be going back to windows, I installed Dapper.

I went to install the 686 kernel and it wouldn't work.  It would boot fine, but the keyboard wouldn't work.  This led me to believe the 2nd core was bad.

I left the machine running the 386 kernel and have been a fairly happy camper.    I eventually upgraded to Edgy via doing a dist-upgrade and have been keeping it reasonably up to date.   But with the pain of VMWare having to reconfigure every time you changed kernel's I had not applied the last Edgy Kernel.    I decided I wanted to upgrade to Gutsy.   So I did a dist-upgrade to Feisty.   When it went to reboot, it locked up during the boot process, very shortly into the progress bar.   If I let it set a long time, I get a couple of errors about ATA channel 1 and 2 timing out or having errors (there is a SATA drive in the system).   Mind you it was working fine.   I've tried to boot Gutsy, Feisty, and Edgy live CD's and they all hang at the same point (and Edgy was working on the hard drive).   I can boot a Dapper Live CD or I can boot off of the Edgy hard drive IF I go back to the 2.6.15 kernel instead of 2.6.17 or later.   I've tried putting nosmp in the boot file in case the 2nd processor was causing the problem and that didn't help.   

I can't find any good diagnostics to figure out what the problem is.   I want to get the machine back in service.   Booting 2.6.15 isn't going to work because almost all the software is expecting a later kernel (gcc for instance is expecting a later kernel and I can't rebuild the vmware server, etc.).

So I'm hoping someone can point me to a changelog of what changed between 2.6.15 and 2.6.17 to see if that can help me narrow down what's busted on the computer.    Being two years old, its going to be hard to swap out a lot of parts and I really can't afford to buy a new computer at the moment.

So if any one can point me to differences between the kernel's that could be causing my problems, I would appreciate it or if any one has seen a similar problem and can advise.   I'm thinking about trying to install FreeBSD and see if that solves it, but I would rather stay in the Ubuntu family if possible.


Thanks
Rob

---

### Post by robmiracle on 2007-11-22
I went into grub's menu.lst tonight and removed the quiet option to see what the kernel was spewing during boot.   As a summary, no kernel 2.6.17-10 or later will boot up.   A 2.6.15-20 something will boot up.

Any way, there were a set of errors and odd messages that may be a clue to the problem.   I assume the [   66.293xxx ] type number is the seconds after boot and I won't include them here.  Its a little hard to screen grab at that point :-)

ata3.00 qc timeout (cmd 0x27)
ata3.00 ata hpa_resize 1: sectors=488397168, hpa_sectors=0
ata3.00 failed to set xfered ?? (can't read my handwriting) (errmask 0x40)
ata3.00 disabled

This repeats twice, about about 60 seconds later.   It appears to probe the machines CF/SD card reader fine (though it appears to do it twice).  

Then there is these messages:

ata: abnormal status

Check root= bootarg  cat  /proc/commandline
or missing modules, devices: cat /proc/modules ls /dev

ALERT!  /dev/disk/by-uuid/fb444af4-46f0-480a-8f41-b5657f015ac4 - does not exist.  Dropping to Shell


Now I can boot under 2.6.15-27 (I think) and run.  I can mount /dev/sda1 where my main / partition lives.   I don't know what really works and what does't because I had tried to upgrade Edgy to Feisty when this problem started.   So i'm not sure what I can attribute to hardware and what to software while running under this old kernel.     Since I can mount the drive, that doesn't seem to be a problem with the hardware.    Since Live CD's don't touch the CD and they experience the same problem, I'm suspecting some incompatibility or something else.

Its an HP Media Center PC m7170n and pretty much stock.   I did put a Hauppage 350 TV reader in it to replace the one that was there.    But it was running fine under that hardware.


Help!!!  Thoughts!!!!

Thanks
Rob

---

