---
title: "grub error"
date: 2007-04-22
forum: General Help
---

### Post by mahiyar on 2007-04-22
Hi, So to celebrate the feisty launch I bought a shiny new SATA disk. My current configuration is Ubuntu edgy sharing windows on 80gb ide, working perfectly. I disconnected the ide drive connected the sata and installed feisty on it, installed perfectly without any problem, now I reconnect the ide drive make it the 1st drive to boot and still no problems, I can boot both into edgy and windows. Now I want to boot into feisty by modifying the grub menu.lst of my ide, so I add this to my menu.lst

title           Ubuntu Feisty Fawn
root            (hd1,0)
savedefault
chainloader     +1

However on restarting and selecting Feisty I get "cannot mount selected partition error".

On choosing the sata as the first disk to boot I can boot into feisty.

Any help will be much appreciated

---

### Post by mahiyar on 2007-04-22
I even tried adding the line (hd1) /dev/sda in device.map, but the same error. However after giving t he error it does go in to the grub menu of the sata/feisty drive giving options but on selecting same error repeats.

---

### Post by forlaf on 2007-04-22
Hello,
I'm not certain of this--I don't boot Windows, but I think you need two more lines on your grub entry:
   kernel   /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb1 ro quiet
   initrd    /boot/initrd.img-2-6-20-15-generic

This is if you are using the generic kernel, and you need to change the "sdb1" to reflect the boot partition for your Feisty install. I have two hard drives, and "sdb" is the second (sda is the first). On my second hard drive, I have Feisty booting on the first partition (this is the default).

Good luck,
David.

---

### Post by confused57 on 2007-04-23
> **mahiyar said:**
> Hi, So to celebrate the feisty launch I bought a shiny new SATA disk. My current configuration is Ubuntu edgy sharing windows on 80gb ide, working perfectly. I disconnected the ide drive connected the sata and installed feisty on it, installed perfectly without any problem, now I reconnect the ide drive make it the 1st drive to boot and still no problems, I can boot both into edgy and windows. Now I want to boot into feisty by modifying the grub menu.lst of my ide, so I add this to my menu.lst

title           Ubuntu Feisty Fawn
root            (hd1,0)
savedefault
chainloader     +1

However on restarting and selecting Feisty I get "cannot mount selected partition error".

On choosing the sata as the first disk to boot I can boot into feisty.

Any help will be much appreciated

See the configfile method in this link:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

The chainloader method will work if you install grub to the root partition, but I'd give the configfile boot method a try.

You could boot into Edgy beforehand and check the output of "sudo fdisk -l" to determine for sure where your Feisty root partition is.  

Added:  Since you installed Feisty on your SATA drive with your IDE drive disconnected, your root partition was recognized as (hd0,0) by grub; but when you reconnect your IDE drive & boot first to it your Feisty root partition would be (hd1,0) to grub.

What you would probably need to do is boot into Edgy and mount your Feisty install and change the root from (hd0,0) to (hd1,0):
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Then add the configfile entry to your Edgy grub menu, then try to boot into Feisty.
You'll also need to change the groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by mahiyar on 2007-04-23
Thanks confused, wish you a speedy recovery, but try as I might I could not get the SATA to boot from my ide. I tried to boot from grub CLI. The geometries and other commands worked well from CLI, the moment you try to boot, it returned error 17. Even the basic step of "direct kernel boot" from CLI stopped midway at the point of recognizing USB devices. I think that's where the problem lies somehow grub mixes between USB and sata drive?

So I turned logic on its head and made SATA the 1st boot device, modified the menu.lst of SATA and now everything works windows and all.

Thanks again

---

### Post by confused57 on 2007-04-23
> **mahiyar said:**
> Thanks confused, wish you a speedy recovery, but try as I might I could not get the SATA to boot from my ide. I tried to boot from grub CLI. The geometries and other commands worked well from CLI, the moment you try to boot, it returned error 17. Even the basic step of "direct kernel boot" from CLI stopped midway at the point of recognizing USB devices. I think that's where the problem lies somehow grub mixes between USB and sata drive?

So I turned logic on its head and made SATA the 1st boot device, modified the menu.lst of SATA and now everything works windows and all.

Thanks again

Thanks, I'm doing much better...good job getting your system booting from one hard drive.  I'm not sure why it didn't work booting first to your IDE, may be a Feisty difference I'm not aware of & yes, everything should work in reverse(booting first to your SATA).  I believe you have a very good understanding of how grub works to successfully set your system up this way.  I'm still adjusting to the UUID's used by Feisty & Edgy.

---

