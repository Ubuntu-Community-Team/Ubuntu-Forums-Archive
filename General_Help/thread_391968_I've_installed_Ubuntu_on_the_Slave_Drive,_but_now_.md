---
title: "I've installed Ubuntu on the Slave Drive, but now Windows won't boot from the Master"
date: 2007-03-23
forum: General Help
---

### Post by Darkness Flame on 2007-03-23
Well, after going through hell just to get the second hard drive to come up and register as the primary slave hard drive, I then also had to get Ubuntu to boot from the CD. Luckily, that was easy. I go to install Ubuntu on the Primary Slave Hard Drive (Trying to keep Windows on the Primary Master) The first time, the install didn't work. I assume that this was because I tried to partition the hard drive with windows, and it would, but it wouldn't format it. When I tried to install Ubuntu again, I selected the slave drive, and then selected to format it and create a new partition. 

After that install, I restarted my computer and removed the CD, however, I couldn't get either Windows, nor Ubuntu to work. I went through BIOS to try and boot normally, as well as from the Primary Master, but both times, it said something about "GRUB version 1.5" and then come up and say, "Error 18" I tried running diagnostics on the drive, but it did the same thing, except saying "Error 21". Whenever I tried to boot straight from the Primary Slave drive, nothing would happen. I had to re-insert the Ubuntu CD and boot that to be able to get anything to work. Thing is, Live CD won't show me anything on any of those hard drives (I'm not sure if it's meant to do that or not, ...) Help, please?

Also, I am doing this on a Dell 4600(i). On top of that, I don't think the data on my primary master drive would have been lost, because the installation would have taken much longer. (formating 20 GB in half an hour? sounds quite a bit short for these IDE drives.)

---

### Post by crispy_420 on 2007-03-23
Sounds like you messed up the master boot record and if grub does boot up, it does not know where to look for the OSs. Search these forums with this knowledge, I can't help you as I don't have the experience needed. But someone else may. Good Luck...

---

### Post by dcstar on 2007-03-23
> **Darkness Flame said:**
> Well, after going through hell just to get the second hard drive to come up and register as the primary slave hard drive, I then also had to get Ubuntu to boot from the CD. Luckily, that was easy. I go to install Ubuntu on the Primary Slave Hard Drive (Trying to keep Windows on the Primary Master) The first time, the install didn't work. I assume that this was because I tried to partition the hard drive with windows, and it would, but it wouldn't format it. When I tried to install Ubuntu again, I selected the slave drive, and then selected to format it and create a new partition. 
........

It may be best to unplug the Windows drive and just do the Ubuntu install on a single connected hard drive.

The Grub error may be the one where the boot loader code is not within the first 1024 cylinders of a disk, this may be due to the problems you had with the initial formatting.

If you don't mind spending the time, wipe the existing Linux partition and start the install again with an empty drive, it may work a bit better and you can manually add in the Windows disk later.

---

### Post by Darkness Flame on 2007-03-24
> **dcstar said:**
> It may be best to unplug the Windows drive and just do the Ubuntu install on a single connected hard drive.

The Grub error may be the one where the boot loader code is not within the first 1024 cylinders of a disk, this may be due to the problems you had with the initial formatting.

If you don't mind spending the time, wipe the existing Linux partition and start the install again with an empty drive, it may work a bit better and you can manually add in the Windows disk later.

Well, I've restored the MBR, and so now Windows is back up in running. I found out that it overwrote the MBR in the first place because I didn't have a Boot Manager. I'm going to download one tomorrow, format that hard drive, disconnect the first, and then install it again. The Boot Manager, unless I'm mistaken, should allow me to choose which one I want, rather then having to go through BIOS. 

Overall, thanks to both of you.

---

