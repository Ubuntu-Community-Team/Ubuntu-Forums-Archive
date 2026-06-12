---
title: "Package repair destroyed GUI"
date: 2007-11-11
forum: General Help
---

### Post by syaoran05 on 2007-11-11
I just installed Ubuntu Feisty last night, dualbooting with XP, without problems.

However, my screen resolution was stuck to a very small 800x600 (which even obscured the bottom part of the installer).

I have a GeForce2 MX/MX400 graphics card, which is quite old (this machine is about 5-6 years old now). Ubuntu searched for a driver for my card, and it installed a generic (i think) "non-free driver" for it. But still, i couldnt set my resolution beyond 800x600. By the way, i still use a CRT monitor.

I looked for a way to get an "official driver" and i stumbled upon Envy, so i installed that, and it did what it was supposed to do EXCEPT get me my driver. So what i did was go to NVIDIA's site (which stupidly, i didnt think of before), and downloaded the driver for my card. The only problem was, when i clicked on the installer thing, Ubuntu said it was encoded in something it cannot understand (we're talking the Unicode and that kind of "encoding"). I gave up, and instead looked for a way to change the resolution.

I found a guide in the Ubuntu Help site, which told how to make the screen resolution bigger. It involved running an automatic recheck on the system so that it will detect the proper settings. But when i went to that part, there was no option for an automatic check, and i had to go through it manually, the screen, mouse, keyboard -- everything.

The fix did work, and i got the 1024x768 resolution that i wanted, but this time, the titlebars were gone when Desktop Effects was on, and the terminal was nothing but a big white square. I turned off the Effects and looked for a way to restore the title bars. I found a guide which made me add two options to the xorg.conf file. It worked, and i had a 1024x768 screen with desktop effects.

I wanted more, so i thought of getting Beryl. The guide told me to run a deb command followed by a url then something. It didnt work, so i just downloaded the tarballs in the beryl site. I didnt know what to to with them, so i tried running Add/Remove, and see what will happen, and it told me that i have two broken packages in the system and i should fix it in Synaptics.

So i opened synaptics and fixed the two packages. Synaptics told me that it was fixed and i had to reboot.

I rebooted and i was greeted with errors and a "windowed prompt" made of ASCII saying that X11 was busted and well obviously, the GUI wont work.

I tried rebooting to XP: i had GRUB hidden, and when i saw GRUB there were two additional entires to the OS list, which are doubles of Ubuntu and Ubuntu in generic mode. This machine is a family machine, and keeping Linux invisible was a prime concern, so in panic i did a FIXMBR using the XP installer cd deleted GRUB.

In XP, i wiped out the linux partition into unallocated space. there are two problems i face now. there's a free space of about 450++MB, and it wont become unallocated (its possibly the swap partition), and a mysterious 640GB (yes, Gigabyte) partition after the last partition in my hard drive (which is NTFS, and im sure it cant have any partition after it coz its the absolute last). I only have 40 GB of hard disk space.

[IMG]http://srv0106-06.oak1.imeem.com/g/14bd33799a2fcba25564cee8075b4c6a.jpg[/IMG]
By the way, im pretty sure that the **Local Disk (D:) was previously 20GB, and now it shrunk to 17.**

now my questions:
What did i do wrong, that X11 went busted?
Why were there broken packages, even if i didnt modify them?
What did Linux do to my hard disk partitioning? What can i do to fix this?
Will deleting the 640GB partition possibly wipe out my whole disk?

---

