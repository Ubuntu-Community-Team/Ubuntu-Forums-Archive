---
title: "Feisty, VMWare Server and Win2000...."
date: 2007-07-19
forum: General Help
---

### Post by willbur on 2007-07-19
Hi all

I have a standard Feisty install and have just installed VMWare Server from the commercial repository. When i put my Win2000 CD in the drive to create a Windows virtual machine, I'm told that the hard disk format is incompatible with windows, and i am given the option to let windows reformat for me.

I let Ubuntu format the drive for me at install (ext3)...

Any ideas? has anyone done this?

many thanks in advance....

---

### Post by dabl on 2007-07-19
Yikes -- you're looking at Win 2000's message, not VMWare's!  During installation on a Windows virtual machine, the real hardware in your computer is NOT formatted, only the "virtual" machine's hard drive is formatted.  Do you have a virtual machine to start with, or are you creating one from scratch?

I use VMW Player, not Server, so I'm not sure exactly what you need to do, but be careful there or you're going to be an ex-Ubuntu user!  :)

---

### Post by ali4949 on 2007-07-19
hi there
I have the same setup. Feisty with vmware server. When you go into the vmware server console, you create a virtual machine and it asks you all the questions as to what size you want to allocate to the disk. this disk is just file on your ubuntu partition, and when you install windows virtual machine, the install will format that drive(file) so you don't have to worry about it. The wizard is pretty straight forward and if i remember correctly once you power on the virtuall machine, it will look in the cd rom drive and look for the bootable image to install and then you are on your way.
also check out this other thread::
[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+how+to](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+how+to)

good luck

---

### Post by willbur on 2007-07-19
Yes, I'm looking at Win2000's message in the VMWare console when I'm installing the OS from my old Windows CD....

---

### Post by willbur on 2007-07-19
Thanks, ali4949. So the windows installer will format my pseudo HDD (ie a file created by VMWare) to, say ntfs or FAT32 so that windows can be installed on it, without touching the underlying drive structure on my lovely ext3 hard disk. Is that correct?

---

### Post by willbur on 2007-07-19
Whoops - I forgot to thank dabl for his reply. All help is very much appreciated, and is one of the best bits of being an Ubuntu user :)

---

### Post by dabl on 2007-07-19
You are very welcome -- not much help there, I just didn't want to accidentally lose a Ubuntu installation! :)

---

### Post by willbur on 2007-07-20
Sorry, everyone, but can you please confirm that if I let my win2000 install cd run it's format program whilst running inside a VMWare virtual machine, it'll only format the folder allocated to it by VMWare, not my entire hard drive? I'm installing win2000 from scratch, not simply importing a premade win2000 virtual machine, if this makes a difference. It's important I get this bit right - I don't want to be an ex Ubuntu user :wink:

---

