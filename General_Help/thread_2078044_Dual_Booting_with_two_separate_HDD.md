---
title: "Dual Booting with two separate HDD"
date: 2012-10-30
forum: General Help
---

### Post by jacksonleigh on 2012-10-30
Hi everyone

I was just wondering if there is a way to dual boot between Windows 8 and Ubuntu by selecting HDD on boot instead of selecting the OS through grub.
In other words, I want to have two HDDs each with their own bootloader and OS (one linux one windows) and each HDD takes me directly to their OS. 
I would have the Windows HDD as the default boot drive and it always just boots as if Linux isnt installed. Then on the occasion that I want Linux, I boot form the other HDD and it boots directly into Ubuntu as if Windows isnt installed.

Thanks!

---

### Post by houseworkshy on 2012-10-30
If you are talking of a removeable hard drive then you could simply have it at the top of the list in bios ( assuming bios ).  When it is present it would be the boot disk when absent the windows drive would be.
If both drives are installed in the machine all the time wait for more informed advice.  
That said.  I have a duel hard drive machine though both drives are now linux, one of them used to be vista, and grub does work a little like that anyway.  The bootloader is always on one drive but when I bootup and choose the other drive,  once in, the drive with the loader is unmounted so they do work as differant systems.  In my windows days grub would do it's stuff only as far as giving me the choice then hand over to the windows bootloader and get out of the way.

---

### Post by Rexilion on 2012-10-30
That should be easy to do. The trick is to only attach the HD you are installing your OS on. Something like this:

- Connect ***_only_*** disk 1: install Windows
- Connect _***only***_ disk 2: install Ubuntu

Connect both.

With Ubuntu, it's not strictly necessary to connect only the second disk since you can select where you want to your bootloader installed (i.e. MBR first/second disk or a partition (used for chainloading)). But doing so will make it less likely to fail.

Windows Setup on the other hand is kind of stubborn and I have heard stories of it using 'obscure' partition setups and overwriting bootloaders. Hence, this system is geared towards regular end users so most ppl don't bother anyway.

---

### Post by shreepads on 2012-10-30
> **Rexilion said:**
> That should be easy to do. The trick is to only attach the HD you are installing your OS on. Something like this:

- Connect ***_only_*** disk 1: install Windows
- Connect _***only***_ disk 2: install Ubuntu

Connect both.

With Ubuntu, it's not strictly necessary to connect only the second disk since you can select where you want to your bootloader installed (i.e. MBR first/second disk or a partition (used for chainloading)). But doing so will make it less likely to fail.

Windows Setup on the other hand is kind of stubborn and I have heard stories of it using 'obscure' partition setups and overwriting bootloaders. Hence, this system is geared towards regular end users so most ppl don't bother anyway.

I would suggest keeping the first Windows disk plugged in while installing Linux (but take extreme care not to install grub on the windows disk).

The reason being that say you have 4 SATA ports, numbered 1, 2, 3 and 4.

You plug the Windows disk in to port 1 and install Win.

Then when you unplug that disk and plug the Linux disk, say in Port 2, AFAIK this would be identified by Linux as the first disk and labelled /sda.

Now when you plug the Win disk into Port 1 later, the Linux disk would be identified as /sdb instead messing up fstab.

---

### Post by jacksonleigh on 2012-10-30
> **shreepads said:**
> I would suggest keeping the first Windows disk plugged in while installing Linux (but take extreme care not to install grub on the windows disk).

The reason being that say you have 4 SATA ports, numbered 1, 2, 3 and 4.

You plug the Windows disk in to port 1 and install Win.

Then when you unplug that disk and plug the Linux disk, say in Port 2, AFAIK this would be identified by Linux as the first disk and labelled /sda.

Now when you plug the Win disk into Port 1 later, the Linux disk would be identified as /sdb instead messing up fstab.

Can someone please advise on this?
They are both installed harddrives and ideally I would like to only have one hard drive in at a time during the installs. Like mentioned before, this would give the best chance of sucess.
But if this will give me issues afterwards, then clearly I cant do that

---

### Post by Rexilion on 2012-10-30
> **shreepads said:**
> The reason being that say you have 4 SATA ports, numbered 1, 2, 3 and 4.

You plug the Windows disk in to port 1 and install Win.

This is a good suggestion when it comes to Windows. Use the same SATA ports for each disk each time under every configuration. Windows might rely on this since it uses some HAL abstraction layer.

> **shreepads said:**
> Then when you unplug that disk and plug the Linux disk, say in Port 2, AFAIK this would be identified by Linux as the first disk and labelled /sda.

Now when you plug the Win disk into Port 1 later, the Linux disk would be identified as /sdb instead messing up fstab.

That is not true, Ubuntu uses UUID's by default in fstab. Hence, the drives always carry a unique identification. Ubuntu uses these to detect/mount/handle drives. So:

- The order in which these drives are detected does not matter.
- The port to which these drives are connected does not matter.

So, only when installing Windows use the same port for the same harddisk as it might rely on that. For Ubuntu, this is not a problem, you only have to make sure the disk is connected :)

---

### Post by Mark Phelps on 2012-10-30
I'm one of those folks that uses separate drives and I would disagree with keeping the Windows "drive" connected when installing Ubuntu. It's too easy to accidentally force GRUB into the MBR on the Windows drive when you do that.

I have Ubuntu and Windows on different SATA drives and what works for me is to boot from the Ubuntu SATA drive, run "sudo update-grub" in Ubuntu, reboot -- and then get a GRUB menu containing entries for all the OSs on all the drives.

---

### Post by hal8000 on 2012-10-30
I have two SATA hard drives and the first drive contains Burg Bootloader
(controlled by Ubuntu 11.10)

My second SATA hard drive has Grub2 (courtesy of Ubuntu 12.10).
On a modern BIOS there is a choice to select boot device (without entering full BIOS). On my Award BIOS this is F12.

If I boot press F12, then I can select to boot from CD, Hard disk etc.
If I select hard disk, then the screen gives me choice of either hard drive,
if I select 2nd hard drive I get grub2 from Ubuntu 12.10.

(By default 1st drive is selected and my custom Burg boot loader loads all
OS's)


Yes it is possible to do what you what install windows bootloader into MBR of one hard drive and grub2 into MBR of other drive. Changing drive order at BIOS level or by shortcut F12 (if you have this option) selects which boot loader to use.

---

### Post by shreepads on 2012-10-31
> **Rexilion said:**
> That is not true, Ubuntu uses UUID's by default in fstab. Hence, the drives always carry a unique identification. Ubuntu uses these to detect/mount/handle drives. So:

- The order in which these drives are detected does not matter.
- The port to which these drives are connected does not matter.

So, only when installing Windows use the same port for the same harddisk as it might rely on that. For Ubuntu, this is not a problem, you only have to make sure the disk is connected :)

Yes you're right, fstab wouldn't be affected as it's using UUIDs instead of /dev/sda etc, so even though the /dev/sda b naming would change it wouldn't affect fstab...

How about GRUB? I mean when we use the Grub config doesn't it use /dev/sda /dev/sdb instead?

---

### Post by Rexilion on 2012-10-31
> **shreepads said:**
> How about GRUB? I mean when we use the Grub config doesn't it use /dev/sda /dev/sdb instead?

That one crossed my mind as well. But if I'm correct, the HD were GRUB is started from is always denoted as (hd0,..). So that should not be a problem.

---

