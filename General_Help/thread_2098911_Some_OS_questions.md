---
title: "Some OS questions"
date: 2012-12-28
forum: General Help
---

### Post by Nanur on 2012-12-28
Hello everyone!
I just got a couple of simple OS questions.

I have two separate hard drives; one with Windows 7, and the other with Ubuntu 12.10. 
My goal is to get rid of Windows 7, and replace it with Windows 8.

My first question is: How do I stay away from my Ubuntu hard drive, and only deal with my Windows drive?

Second question: Is it possible to replace my Windows 7 directly with Windows 8, using some kind of "Upgrade Installation?"

OR

How could I wipe my current Windows hard drive and replace it with Windows 8? Here I would do end up doing a Windows install after Linux.

Any ideas? I know this isn't directly relating to Linux however :/
Thanks, 
Nanur

---

### Post by lykwydchykyn on 2012-12-28
The simplest answer that comes to mind is to unplug the Linux drive before installing Windows 8.  That removes the possiblity of monkeying with it.

On which drive is your bootloader currently installed?

If you want to wipe out Windows 7, you could always boot up something like darik's boot and nuke to wipe the drive, but I imagine the Windows 8 installer is perfectly capable of reformatting the drive.

---

### Post by Nanur on 2012-12-28
> **lykwydchykyn said:**
> The simplest answer that comes to mind is to unplug the Linux drive before installing Windows 8.  That removes the possiblity of monkeying with it.

On which drive is your bootloader currently installed?

If you want to wipe out Windows 7, you could always boot up something like darik's boot and nuke to wipe the drive, but I imagine the Windows 8 installer is perfectly capable of reformatting the drive.

Oh wow.. brilliant idea about unplugging my linux drive. I will have to do that.

My bootloader is on the Windows drive, since my computer was preloaded with Windows XP. (I know it's an ancient computer, built in 2003 or something, but runs amazing after I upgraded all the hardware.) 

Also, I am sure the Windows 8 .iso will have some kind of upgrade utility. Thanks for the quick reply!

---

### Post by Mark Phelps on 2012-12-28
While you can upgrade Win7 to Win8, you should FIRST go to the Windows 8 forums (eightforums.com) and read through their installation tutorials to see which kind of upgrade you want to perform -- and what the results are of each.

---

### Post by Nanur on 2012-12-28
Honestly, the main reason I want to upgrade to Windows 8, and entirely wipe my Windows 7 hard drive is because when I am on Windows (which is rare) the internet(wifi) crashes, then restarts in about 5 minute increments. I have tried multiple things, and nothing worked. So basically I said screw it, let's start over.
Also I want some kind of Windows for playing some games that don't run so well on Linux.

---

### Post by jim_deadlock on 2012-12-30
After successfully installing your Win8 you can then plug your Ubuntu drive back in, boot it then run

```
sudo update-grub
```

which will add your Win8 to the grub menu so you can dual boot as long as you make your Ubuntu drive the primary boot device (in BIOS).

---

### Post by grahammechanical on 2012-12-30
You might need to re-install the Grub menu. And you might want it on the Ubuntu drive.

In Ubuntu after running

```
sudo update-grub
```

run

```
sudo grub-install /dev/sda
```

if Ubuntu is on drive sda - the first drive. Or,

```
sudo grub-install /dev/sdb
``` 

if Ubuntu is on drive sdb - the second drive. This will install Grub into the MBR of the drive.

Regards.

---

