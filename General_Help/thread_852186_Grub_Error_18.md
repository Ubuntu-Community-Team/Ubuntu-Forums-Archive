---
title: "Grub Error 18"
date: 2008-07-07
forum: General Help
---

### Post by notesetter on 2008-07-07
I've just attempted to set up a dual boot of XP Home SP2 and UbuntuStudio 8.04 and when I try to boot up I get a Grub Error:

"GRUB loading, please wait...
Error 18"

Elsewhere, in the forum archives, it was suggested that it's a BIOS problem (old computer, new HDD) and the solution is to create a small partition on the disk to install the GRUB bootloader. I have the G-Parted live CD and I hope I can use this to do the job. I just want to make sure I do it right. I've spent a few hours now configuring XP and software and I want to fix this without destroying my XP partition.

Anyone willing to help out with this?

Thanks in advance,

Dave

---

### Post by danwood76 on 2008-07-07
Error 18 is to do with an invalid kernel image.
I very much doubt its the old LBA issue, unless of course your PC is over a decade old?
Older PCs couldnt read past a 28 bit LBA and so you can only see a 37 GB drive or something similar.
Now most IDE drives a 48 bit LBA allowing for 137GB drives. (of course now we have a lot larger drives than this also)

It might be that your menu.lst is corrupt for some reason or the kernel image is corrupt.
What did you last do on your Ubuntu install?

---

### Post by notesetter on 2008-07-07
Thanks for the response...

The computer was purchased new in Nov. 2002 and originally came with a 40 GB HDD. I installed a shiny, new 250 GB HDD yesterday and reinstalled XP and some software. Today I attempted to set up the dual boot using the illustrated dual boot page (which went off without a hitch when I followed it to set up an XP/Gutsy dual boot on my laptop). I went through all of the partitioning and setting up a swap, etc using the partitioner from the Ubuntu Studio install disk. Everything seemed to go OK and the install finished smoothly. Only, when I try to boot, I get Error 18.

I sized my XP partition to around 80 GB, and the Gutsy partition is right after that and is around 160 GB. The BIOS does tell me that my hard drive is 137438 MB, so I wonder if having the Gutsy partition going past the 137 GB mark is creating a problem.

---

### Post by prof2019 on 2008-07-07
I just went through this exact experience. I solved it with the following help. The second disk (e.g. sda=1 sdb=2) should be the Linux disk and the first disk (sda) should mount the win XP system. Then the MBR (master boot record) of the sda (or first disk) will include the GRUB for Linux. Hope that helps....it did for me. In other words, install Ubuntu from the ISO CD from the BIOS prompt and the MBR will offer you an opportunity to select sdb for your Ubuntu installation.

---

### Post by danwood76 on 2008-07-07
You might need to update your BIOS if its reporting 137GB.
BIOS updates are normally found on your PC manufacturers website or your Motherboard manufacturers website.

GRUB might be getting funny drive readings from your BIOS, windows boots as its partition is within the 137 GB but as your linux partition is not it probably doesnt like it.
A BIOS update will cure this.

---

### Post by notesetter on 2008-07-07
Thanks,

I'll try to track down the BIOS upgrade for my board. In the meantime, can I delete the extra partitions and remove GRUB to make XP bootable again? That way I can work until I have time to update the BIOS and try reinstalling Gutsy.

I can do the partitions with GParted. But I don't know how to get rid of GRUB.

Thanks, again.

By the way, thanks for reminding me of NOFX. It's been a long time.

Dave

---

### Post by danwood76 on 2008-07-07
> **notesetter said:**
> 
By the way, thanks for reminding me of NOFX. It's been a long time.


Hehe, no problem ;)

You can re-install the windows MBR from an XP install CD under recovery mode by running fixmbr and fixboot. (also possible from a vista CD through the GUI)

It is also possible from the grub live CD though I haven't used it for ages so I'm unsure but if you have an XP CD use that ;)

---

### Post by notesetter on 2008-07-07
Um, I'm having trouble getting into recovery mode. I insert the Windows CD and reboot and press a key to "boot from CD..." Then, I get a message that "setup is inspecting my hardware configuration" or something, then the screen goes dark and stays that way.


Any thoughts?

---

### Post by danwood76 on 2008-07-07
Very odd.
It might be worth waiting for a bit, sometimes it can take a while to wake up.

The alternative is to boot the ubuntu live CD and reinstall the MBR from within there.
This involves a little more effort.

First you have to install the package called 'MBR' using synaptic.
You then need to determin your win boot device, this can be done by listing the partitions with 
```

sudo fdisk -l

```
Your windows partition you may already know but it will be the ntfs one (or fat if you formatted that way)
it will be something like /dev/hda1

To then install the new mbr to load that partition you run the following commnad:
```

sudo install-mbr -i n -e1 /dev/hda

```
(replace the number after the '-e' with the partition number and the '/dev/hda' with the block device name)
Then simply reboot, with a bit of luck it should just then load into windows.

---

### Post by notesetter on 2008-07-16
Well, I've had no luck with the BIOS upgrade. Actually, I successfully upgraded my BIOS, but it still only sees 137xxx MB of storage space on my drive. And I still don't know if this is the issue that fouled up my dual-boot installation (XP accurately reports that my drive is close to 250 GB). So my next course of action is this:

I want to try installing UbuntuStudio 8.04 again to set up the dual-boot, but since I've been working in XP, I'd like to back up my XP partition using G-Parted. Right now, there is about 8.5 GB being used for the OS and all my files. I've installed my old hard drive as a slave and would like to backup the whole partition to that drive. If I do backup my partition to the old drive, and my installation goes bad, and I simply re-copy my XP partition to the front of the new disk, will it be bootable? What are the issues associated with this?

Thanks again,

Dave

---

### Post by Tuliku on 2008-07-16
You have the same issue as i had.

First of all, i suggest you download and burn this:  "Hiren's BootCD 9.5"
Boot from this cd, and wih this you can simply fix your MBR and boot back to windows.

My laptop is from 2005, originally 60 gb disk, but replaced that with a 250 gb disk.
My partitions looked like this:
- 50 gb - NTFS, primary, Windows XP sp3
- 20 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 17 gb - EXT3, logical, kubuntu 7
- 01 gb - Reiser FS, logical, swap

The installing kubutu, it gave me also the grub error 18.

There are 2 solutions for this.

1. Update bios and hopefully it works (i don't think so in your case cause your pc is even older then my laptop)
2. Change the partitions a little.

Option 1 didnt work for me, because there simply was no newer bios update avilable.
Option 2 worked for me without problems, and kept my windows intact.
To change the partitions, i used "Paragons Partition Manager 9".

The following change was made, resizing my windows xp partition, 2 gb smaller, and place the 2 gb as first primary partition for the root.
Now my setup looks like this:
- 02 gb - EXT3, primary, Ubuntu (root, basic libraries)
- 48 gb - NTFS, primary, Windows XP sp3
- 20 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 17 gb - EXT3, logical, Ubuntu (other libraries)
- 01 gb - Reiser FS, logical, swap

And now it is working perfectly for me.

In my thread where i asked for advice about a fresh install (and received great help) you can read a bit more about my partition setup etc.
Have a look, it might help you:   [http://ubuntuforums.org/showthread.php?t=859124](http://ubuntuforums.org/showthread.php?t=859124)

Good luck

---

### Post by Tuliku on 2008-07-23
I guess you solved your issue, cause there is no feedback at all.

---

