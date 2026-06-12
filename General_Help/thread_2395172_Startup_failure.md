---
title: "Startup failure"
date: 2018-06-27
forum: General Help
---

### Post by roachkv2 on 2018-06-27
I've searched for hours but can't find anything specific to my situation.  I've also tried many "fixes" to no avail.  

I'm on 16.04.  When I try to start my system, I get stuck at the attached splash screen (which has a purple background in my case, FWIW).  I've even left the system on for, literally, a week and cannot get past this screen.

I can get to GRUB fine. I have three or so kernels, all of which I've tried, both in normal and recovery mode.  I have booted into recovery mode and run "clean", "dpkg", and "fsck"; all run fine and return no errors that I can ascertain.  When I drop to a root shell, I can see my hard drive, with all the partitions I created.  When I peruse the file system, all files seem to be in place.  

When I boot up the live CD (16.04), I can still see my hard drive.  Gparted shows all partitions are there and working.  And I can use the file browser to look through everything.  It is my understanding, that if I elect to "install" Ubuntu from the live CD that it will detect my previous installation and proceed with a repair of the OS.  But when I choose install, it tells me there is no identifiable file system (even though I can see it with the file browser).  Of note, I chose to use LVM when I installed 16.04 (it was a clean install), and I probably should not have since I really have NO idea how it works.  

I have also somehow ended up in emergency mode a couple times but can not remember how I ended up there.  At any rate, I've run journalctl the times I made it to that screen, but I could never find any error messages in the logs that would explain what is happening.

Everything is backed up, and I COULD reinstall then restore my backup, but I'd rather try to figure out what's happening. And BTW, on a 1-10 scale of Linux knowledge with 10 being Linus, I'm probably a 6-7.

Thanks for your help

---

### Post by westie457 on 2018-06-27
Welcome to UF roachkv2

What I know about LVM could be written on the head of a pin using a large paint-brush and capital letters, there would still be a lot of pin uncovered.

Maybe Testdisk can help. Take a look at this link for some pointers. [https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=618](https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=618)

---

### Post by Cavsfan on 2018-06-27
LVM may not be the best way to go. My Arch Linux install tells me a message when booting that "LVM is disabled by bios".

Once I looked up what it was I left it alone and ignore that message. I'm using GUID/GPT partitioning on a SSD.

If LVM is what is hindering you, you may not need LVM, here are a couple of links:  [https://www.quora.com/What-are-the-disadvantages-of-LVM](https://www.quora.com/What-are-the-disadvantages-of-LVM)

[https://www.linux-tips-and-tricks.de/en/general/282-was-kann-lvm-und-warum-sollte-man-lvm-benutzen-what-can-lvm-do-form-me-and-why-should-i-use-lvm-2](https://www.linux-tips-and-tricks.de/en/general/282-was-kann-lvm-und-warum-sollte-man-lvm-benutzen-what-can-lvm-do-form-me-and-why-should-i-use-lvm-2)

---

### Post by roachkv2 on 2018-06-27
Thanks, westie457.

I mentioned LVM just in case that has something to do with the boot process not completing.  However, unlike in the link you provided, I can, in fact, see my partitions (or should I say logical volumes??).  And if I wanted, I could copy all the files off the disk onto another disk after booting up using the live CD.  


And thank you too, Cavsfan.  Your first link definitely had me nodding my head in agreement.  Next time I do a new, clean install, I am going to ditch LVM.  For the time being, though, I'm stuck with it, and again, I'm not entirely sure that LVM is where the problem lies.

Your help is greatly appreciated as I try to figure this out!

---

