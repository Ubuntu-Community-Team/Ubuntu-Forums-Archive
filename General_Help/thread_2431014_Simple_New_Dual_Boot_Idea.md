---
title: "Simple New Dual Boot Idea?"
date: 2019-11-10
forum: General Help
---

### Post by MarkX on 2019-11-10
I've been using Lubuntu for years but now need to have one machine dual booting with the intrusive spyware that is MS Windows 10. 
Rather than doing it the software way I was thinking of just having separate hard drives for each OS and installing a simple electrical changeover switch on the power lines from the power supply to the ssd drives to power up either one or the other drive.
The sata data lines would remain plugged in to separate sata inputs (obviously).

1) Am I missing something or would this be a much safer and more practical way of dual (or multi-) booting altogether? 

2) The selection would happen before the computer is switched on but what would happen if the drive selection switch is flicked after computer power up?

3) What would be the BIOS or UEFI settings?

---

### Post by Skaperen on 2019-11-10
2.  lots of problems can happen, from crazy controller state because one voltage is still bouncing on and off when the other is stable, to physical damage by the line capacitance driving an over-voltage lead surge.  then there is the risk of sector recording damage to the drive being cut off while in the middle of writing a sector requiring it be low-level formatted at the factory.

---

### Post by Skaperen on 2019-11-10
the simplest way to dual boot is to use a 2nd computer.

---

### Post by MarkX on 2019-11-10
OK, maybe have the switch recessed so it doesn't get flicked by accident.
(Are SSD sata drives hot-pluggable?)
The 2nd computer idea is a tad expensive, lol!

My new setup uses a 43" 4k TV screen as the monitor (set to low-lag gaming mode). I want to  keep Windows 10 accessible  for potential  gaming (and because I paid for it) if I can't get wine or whatever to work but I also want to have Ubuntu Studio as the main OS. 
I just don't trust the... "folks" from Microsoft not to mess up my Linux software. The sheer massive scale of M$ intrusiveness, manipulation and greed was quite an eyeopener after not using Windows for years. No way am I using M$ for regular internet access!
 So... A switch kit to fit into a front drive bay to select the boot drive to use would be a nice new product. I suppose it could have some built-in safeguards, if needed.

---

### Post by oldrocker99 on 2019-11-10
The biggest problem with dual-booting Windows and Linux is that one of the self-rebooting "updates," because "Windows cannot update files while they are in use." The boot sector can be overwritten, which requires boot-repair. It's a pain.

Linux can easily update files which are in use, by stopping that process, updating the file, and restarting the process.

Duh.

---

### Post by crip720 on 2019-11-10
If drives are easy to get at and remove, just have ubuntu and windows on separate drives and just use one at a time. Remove the one you are not using.   Could also place one on a USB drive.  Don't think you can only switch power on or off for a drive with data lines still connected safely.

---

### Post by MarkX on 2019-11-11
I just read that hot plugging capability is actually part of the SATA specification. 
In any case, it wouldn't actually be hot plugged, one would simply switch to the wanted SSD drive before turning on the computer. Any hot plugging would only happen by accident.

Yes, I suppose alternatively one could just have one power and one SATA cable outside the computer. That would work. 
I actually have cables which have both combined in one plug. (One could even make a special bay for it like the old PCMCIA ones.)

But if the switch idea works, that would get rid of any software booting problems and boot with as many drives/OS's as your motherboard has plugs for.

---

### Post by dragonfly41 on 2019-11-11
I have a Dell 3268 which came with Windows 10 OEM installed. I installed Ubuntu in a resized partition but I do not boot into Windows 10 for the reasons given by @oldrocker99. That is, on a major upgrade Windows disregards any alien partitions such as ext4 and the Ubuntu shared installation can be lost. No principle of "duality" here. Windows is the cuckoo in the nest and throws out Ubuntu settings.

I purchased a few akasa USB containers and placed old Ubuntu installations in there in dedicated drives.

Also I have a USB port expander (expands to 4 ports) permanently plugged into my tower and I can quickly reconfigure external USB containers and restart my tower.  In BIOS (press F2 at bootup) the boot sequence has Ubuntu first and Windows second.

I intend to move my internal Ubuntu at a convenient time (upgrade) and leave Windows in its own drive.

---

### Post by jetsam on 2019-11-11
I think it may be a bit...  (thinking of a polite way to say it)...  "overly optimized" to actually need to physically remove the second drive just to be sure Windows doesn't get up to any silly games with your Linux install.  You can safely leave both disks mounted in either boot mode and just find a reasonable boot menu to allow you to switch between Windows as prime OS and Linux as prime OS.  

I used to do this with a (3 and 1/4") floppy that I installed a boot manager on.  It was actually a nice little privacy guard that way: If I took the floppy out, the system wouldn't boot at all and would just seem broken to any would-be unauthorized intruders.  There are loads of other options for a single boot manager, though, and it could of course reside on either hard drive or an ssd boot partition.

The advantage to mounting both drives at once is that you can share files between the systems, back them both up online or offline, basically access all your files however you want to.  Although I _could _see Windows messing up a boot partition, you should be able to recover from that if it does.  I doubt very much that Windows will touch what it will usually see as a data only, second hard drive with a Linux partition or two on it.  

Microsoft, though, does have ways of surprising me at times.  ;)  

The drive swapping solution is fine; it can work, and it isn't very expensive to get good hot swap mounts.  It's just, possibly, though, overkill for the average user and for your use case in particular...

Cheers,
jetsam

---

### Post by sdsurfer on 2019-11-11
The dual boot with grub is simple enough, no reason to over engineer it. :-) I have two drives, one Windows, one Linux, the way I set it is to default to Ubuntu unless I tell it to go into Windows. There is a 30 second menu on startup, I suppose that can be eliminated if needed.

---

### Post by Frogs Hair on 2019-11-11
> **oldrocker99 said:**
> The biggest problem with dual-booting Windows and Linux is that one of the self-rebooting "updates," because "Windows cannot update files while they are in use." The boot sector can be overwritten, which requires boot-repair. It's a pain.

Linux can easily update files which are in use, by stopping that process, updating the file, and restarting the process.

Duh.

I resolved the update issue by using EasyBcd software in Windows which grants access to the Windows boot loader. I'm on my second build of Windows 10 on two machines and updating fine. The software _does not_ work with all Linux distributions , but seems to work well with Ubuntu. When booting grub appears first and when Windows is selected it opens the metro boot-loader. I also set Windows to boot first. I have not experienced overwrites of any kind and this includes installing daily builds on my testing computer.

---

### Post by Autodave on 2019-11-11
You can disconnect your Windows drive.  Connect your drive to install Linux on.  Boot machine and install Linux.  Power off.  Connect Win drive while leaving Linux drive connected also.  Boot machine.  Enter "Select boot order" (or something to that effect) and choose which drive to boot to.  I have mine set up that way.  I power on, hit F11, choose which drive that I want, and it boots to the correct OS.

---

### Post by Frogs Hair on 2019-11-11
> **Autodave said:**
> You can disconnect your Windows drive.  Connect your drive to install Linux on.  Boot machine and install Linux.  Power off.  Connect Win drive while leaving Linux drive connected also.  Boot machine.  Enter "Select boot order" (or something to that effect) and choose which drive to boot to.  I have mine set up that way.  I power on, hit F11, choose which drive that I want, and it boots to the correct OS.

If I had a spare drive lying around I would be doing this for sure on the desktop. :)

---

### Post by TheFu on 2019-11-11
I don't dual boot.

There are disk chassis with removable front access available for 3.5" SATA drives.  I have one of these: 
[https://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/](https://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/)  There are also external disk arrays with eSATA which work in a similar way.

A friend swears by EasyBcd.  I know nothing about it.

I run Windows inside a virtual machine with Ubuntu as the hostOS.

---

### Post by hk42 on 2019-11-12
Why do you talk of dual boot when there are so many variations of Windows ,Linux and Android ?
Why do you want to use separate disks when 10TB one's are available and UEFI allows many partitions ?
Even installation media can be multi-boot :
[https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso](https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso)

---

### Post by Frogs Hair on 2019-11-12
> **hk42 said:**
> Why do you talk of dual boot when there are so many variations of Windows ,Linux and Android ?
Why do you want to use separate disks when 10TB one's are available and UEFI allows many partitions ?
Even installation media can be multi-boot :
[https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso](https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso)

Looks interesting, how do you verify the origin of any of the software being downloaded especially the Windows ISOs ?

---

### Post by hk42 on 2019-11-12
I have not tried it yet.
But the idea of switching hard drives is not "new" and even floppy disks 
allowed that.
Now any installation that requires an internet connection is a BIG 
security risk.

---

### Post by MarkX on 2019-11-17
Thanks everyone for contributing your thoughts.
I have not actually tried the idea yet but a physical selector switch must be the safest and simplest way to have multiple OS's on the same computer. I have had problems with Grubs, updates, recoveries, moving everything when computers die etc. etc..
I certainly do not want anything to do with Micro$oft infesting my computer if I can advoid it. It is ridiculously untrustworthy software and that means having it physically switched out until absolutely needed. 
Drive switches would also isolate other software from Windows while it's running.
In fact a physical electrical switch on auxiliary data drives would protect them from M$ infestation and snooping too.
There is simply no way I would want Windows and Linux residing on the same disk. The low cost of SSDs makes that need redundant.
For now, I will just unplug the drives manually (I have some routed outside of the computer) but if a functioning drive selector switch were to appear on the market, that would be a product I would immediately buy. Stuff doing it in software or BIOS/UEFI.

---

### Post by jetsam on 2019-11-19
The switch is not a difficult ECE design challenge, but it's nearly impossible for an amateur to implement correctly.  The risk of data loss is just too high; don't do it.

Buy a hot swap mount and two hard drives.  This will do everything you want it to, I think...

Edit: You could also consider network booting for super powers...

---

