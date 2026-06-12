---
title: "Restoring drive image to SSD bootloader question?"
date: 2015-06-04
forum: General Help
---

### Post by einstein**-7 on 2015-06-04
Hey there,  I've been working all day trying to get various programs to clone an existing ubuntu system on a 500GB HDD with only 70GB used to a 240GB SSD... 
Finally decided to simply use the ubuntu "disk utility" to backup an image of the filesystem partition and then restore it to the new drive since all the cloning software sucks and lacks the ability to not copy unused bytes on the source drive .  
I made the new partion type a Linux and bootable flagged; I also changed the label to "  boot   " but I'm still getting a filesystem missing when booting to it. 
Question is, do I need to install grub to the new drive?  I would think not since the partion that I restored already has grub on it.. ?
How would i go about doing this if the new drive is dev/sda1 ?
Seems like I'm so close, any help would be appreciated.
thanks

---

### Post by Bucky Ball on 2015-06-04
But the grub is in the MBR and you haven't replaced that.

You could try '[Boot Repair']("https://help.ubuntu.com/community/Boot-Repair") and DON'T use the 'Recommended repair' option. Choose to install grub manually and install it to the MBR of sda.

Are you installed in legacy or UEFI mode? It makes a big difference. ;)

PS: [Clonezilla]("http://clonezilla.org/") is the perfect tool for cloning partitions. You can even create .iso files of your current install.

If you have Ubuntu only using 70Gb on a 500Gb drive, any cloning program (that I'm aware of) will require you to clone to a partition the same size, 500Gb, regardless of how much is being used on the source partition. Workaround? Shrink the partitions you are wanting to clone prior to cloning.

---

### Post by einstein**-7 on 2015-06-04
> **Bucky Ball said:**
> But the grub is in the MBR and you haven't replaced that.

You could try '[Boot Repair']("https://help.ubuntu.com/community/Boot-Repair") and DON'T use the 'Recommended repair' option. Choose to install grub manually and install it to the MBR of sda.

Are you installed in legacy or UEFI mode? It makes a big difference. ;)

PS: [Clonezilla]("http://clonezilla.org/") is the perfect tool for cloning partitions. You can even create .iso files of your current install.

If you have Ubuntu only using 70Gb on a 500Gb drive, any cloning program (that I'm aware of) will require you to clone to a partition the same size, 500Gb, regardless of how much is being used on the source partition. Workaround? Shrink the partitions you are wanting to clone prior to cloning.

Ok, I can use Boot Repair from an existing live usb but just wondering where exactly is the MBR of a drive located?  Is it actually a separate small partition maybe hidden?  Sorry if I sound like a newb as you can tell I dont know that much about Master boot records...  
I will attach a image of the new drive..[ATTACH=CONFIG]262428[/ATTACH]

---

### Post by Bucky Ball on 2015-06-04
[This]("https://en.wikipedia.org/wiki/Master_boot_record") might give you an idea. A ton of info out there if you need further detail.

Do you intend installing with legacy or UEFI?

I did something similar to what you're doing a while ago. Cloned (using Clonezilla) the Win and Ubuntu partitions of my 80Gb hard drive and restored them to a new 120Gb SSD. Ran boot repair, done (there might have been a little fiddling with Win, while ago). But I was using legacy. Unsure how you'd go about it with EFI as you need a FAT32 EFI partition (and although Boot Repair is better and improving with EFI I don't know if it's got the capabilities of creating one). 

Hopefully someone familiar with restoring EFI can respond. Might be a matter of creating a small (500mb) FAT32 partition on the SSD prior to restoring the partitions then running Boot Repair and pointing it to that ... or something ... :-k

---

### Post by RobGoss on 2015-06-04
I would have to agree with Bucky Clonezilla is a great tool for cloning your whole system and the process of restoring your system is just as good.

---

### Post by einstein**-7 on 2015-06-04
OK so I ran the Boot Repair from a persistent usb and it put grub on the ssd but the only boot option was to boot back to the USB drive lol! Anyway, just reinstalled grub from the advanced menu and did sudo update-grub and now it works.. Only thing I'm less than enthralled about is that Boot Repair updates the Linux kernel with no option or warning that it is doing so.  Which broke the sys because I have manually installed nvidia drivers and updating the kernel always seems to break the driver but I'll fix that later.

---

### Post by Bucky Ball on 2015-06-04
If your original issue is fixed please mark the thread as solved (see second link in my signature) and post a new thread if you need help with anything else. 

Good luck. ;)

---

### Post by oldfred on 2015-06-05
You only get the issue with Kernel updates & nVidia drivers if you install nVidia drivers directly from nVidia. That should be last choice. 

Better to just install from Ubuntu repository. 
But if a very new nVidia card, you may need the newest driver which is not in repository and then you can use a ppa. 
Links below may show older versions, but the ppas most likely have been updated and include the very latest.

 Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)

 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

      
 nstall Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)

---

### Post by einstein**-7 on 2015-06-05
For future reference others may want to simply boot a regular live ubuntu and install grub that way as it is much simpler and doesn't force you to update the kernel.. But the boot rescue does work just complicated and forces a kernel update which may or may not be desirable depending on your system needs.

---

