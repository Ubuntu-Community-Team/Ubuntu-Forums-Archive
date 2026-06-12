---
title: "[SOLVED] External HD NTFS to FAT32?"
date: 2007-09-22
forum: General Help
---

### Post by Kristopher on 2007-09-22
I have a Maxtor 500GB external HD and i need it in FAT32 so my surround sound system can play the mp3 i put on it.

How do i do this under Ubuntu? also will i need to be root to do this? if yes how do i log in as root and whats the roots password?

I know there is a 4GB limit with FAT32 but i will be moving only a few albums at a time.

Oh am new to Ubuntu so a nice easy step by step reply would be great :-)

---

### Post by ajgreeny on 2007-09-22
You can install gnome-partition-editor from the repos using synaptic, attach the drive and fire up the program you've installed.  In the top right hand corner is a drop down menu of the disks on the machine, so go to the external drive to see what partitions are there.  You can then delete all of it if you want to or reduce it in size and then make another partition of the correct type.

You could also, incidentally, download a copy of Gparted LiveCD and burn that to CD.  It's a great little program and very useful for any partition changes you may want or need to make to your current ubuntu install, which you may not be able to do with the version on the ubuntu liveCD, which is a bit older than the gparted liveCD.

---

### Post by vanadium on 2007-09-22
The 4GB limit is not what you think it is. It means that your files cannot be greater than 4GB. It does not mean that you could not copy more than 4 GB data at one time.

If you want step by step instructions, then post in the Absolute Beginners section. However, I will be a bit forgiving.

Linux is about choice and ajgreeny already gave some options. However, I think that in your situation, the simplest approach is:

* Press Alt+F2, type "gksudo gparted"
* Select your external drive in the dropdown next to the toolbar
* Right-click your partition, select "unmount"
* Right-click your partition, select Format and specify vfat as the file system.

Exit gparted. You will need to disconnect and reconnect the drive for it to automount again.

---

### Post by Kristopher on 2007-09-22
The only FAT options i see are

fat16 or fat32....i take it its FAT32 i select?

Oh and if i ever wanted it back to NTFS, i take it this is possible with just doing another format? 

Thanks

---

### Post by mivo on 2007-09-22
Yes, you can always change the file system (this involves the loss of data on the drive). There are also NTFS drivers for Linux, and ext2/3 drivers for Windows, so FAT32 is not the only available option, but it is easy since you won't need anything else.:9

---

### Post by Kristopher on 2007-09-22
Thanks vanadium that worked 100% wooohoo. Now spending time ripping CDs to it :)

---

