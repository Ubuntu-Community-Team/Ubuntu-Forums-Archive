---
title: "Hardy heron boot problems, possibly grub related"
date: 2008-02-11
forum: General Help
---

### Post by Glowing Fish on 2008-02-11
So a few weeks ago, I switched my sources.list file over, and upgraded to hardy heron, from gutsy.
Everything went fine, until I decided to reboot
(I hadn't rebooted for 98 days, and I imagined I had many kernel upgrades)
When I try to reboot, it gets to grub, and then I get this error message:

Loading, please wait
usplash:  No usable theme found for 1280*1024
screen init failed

And then nothing
I was thinking this is perhaps related to grub still thinking my partitions are located on sda, instead of hda
I tried editing that with a live CD and mounting the disk, but it doesn't seem to help.
Any ideas for relatively simple solutions to this?
If there are none, I will probably just reinstall from a Gutsy CD, when I can get one.

---

### Post by danwood76 on 2008-02-11
well the usplash is failing for starts.
so when you get to grub hit escape and edit the default line so the splash is romoved from the line press enter and try to boot.

see what errors you get then.

and grub looks at the physical disks positions, like hd1,1 as opposed to labels if that helps. but its not a kernel error so that wont be it.

---

### Post by Glowing Fish on 2008-02-11
I actually (temporarily) renamed menu.lst to menu.last, and tried to boot a kernel from grub command line. 
No luck.
Although I didn't write down the specific error message I got at that point.

---

### Post by danwood76 on 2008-02-11
in your original grub list can you boot to your old gutsy kernel? (2.6.22)
also did removing splash from the kernel boot line make any difference.

I dont think the upgrade route is even viable to upgrade to hardy, seeing as its 2 months away and there were a lot of people who reported upgrade problems after gutsy came out.

---

### Post by Glowing Fish on 2008-02-11
I have to get home before I try anything, I am at school right now. 

[http://ge.ubuntuforums.com/showthread.php?t=661116](http://ge.ubuntuforums.com/showthread.php?t=661116)

Someone else also pointed me to this.

I will try both of these and see what works.

---

### Post by Glowing Fish on 2008-02-12
It seems that the splash screen failed might have been a red herring.
When I remove splash, I don't get a splash error, but I do just get a 
"Loading, please wait" error that doesn't seem to go anywhere.

---

### Post by danwood76 on 2008-02-12
what options do you have in your grub list?

it might be worth trying to boot and older kernel version and possibly the recovery mode on any of them.
its not giving any specific error messages which worries me, it sounds like its loading the initramfs but not booting the kernel.

---

### Post by Glowing Fish on 2008-02-12
Well, I posted this in another thread, because I figured out my real problem, which someone else seems to be having.
In the boot process, it gets to

running /scripts/init-bottom

And then, it hangs.

---

### Post by danwood76 on 2008-02-12
It sounds like an initramfs problem.
before the kernel fully boots it loads a ram disk which it extracts the contents of the initrd file (located in /boot) this contains the scripts directory.

The initramfs (called initrd in /boot) loads all the initial stuff required by the kernel to boot.
Its strange that it gives you no other errors, but im wondering if maybe its not being instructed to load the kernel image up.

---

### Post by Glowing Fish on 2008-02-12
It sounds like it isn't just the wrong entry in a text file or something similar

This hard drive is kind of kludgy, its been transported through several systems, and been upgraded since...at least Dapper. 

I think its time for me to get a new, bigger hard drive, put a fresh Gutsy install on it.

Which I have to make another post about...

---

### Post by danwood76 on 2008-02-12
Yeah a reinstall would deffinatly help :)
Sorry it cant be fixed.

---

