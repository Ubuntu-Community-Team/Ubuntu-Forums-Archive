---
title: "Setting up Dual Boot"
date: 2008-05-02
forum: General Help
---

### Post by CuteUsagi on 2008-05-02
Hi everyone!!  I am currently running Ubuntu 8.04 (64-bit) and have unfortunately come to the conclusion that I must dual-boot to windows.  :(  Is is possible to just create a partition and throw windows on it?  It seems to easy...

I have also read that if you're setting up a dual-boot machine with windows, that windows needs to be installed first, but that is not a possibility for me.  Any suggestions???  Thanks!!!!

---

### Post by jaredbuck on 2008-05-02
Wubi might be the easiest way to dual-boot windows and ubuntu without having to mess with partitions. I use it myself to access Ubuntu (until I get a fatter hard drive). You can find Wubi at [http://wubi-installer.org/](http://wubi-installer.org/)

I have, however, had success using a partioner (used BootItNG for that, located here - ([http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)). When I installed a prior version of Ubuntu that way it detected the blank partition and offered to install the OS on that.

Hope my suggestions help.

Jared

---

### Post by enigmaniac23 on 2008-05-02
If you are going to setup a dual boot machine, then in my opinion, it is easier to install windows first.  However, since you already have Ubuntu installed, you might want to take a look at this tutorial on setting up a dual boot with Linux installed first.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by CuteUsagi on 2008-05-03
Thanks for the help!!  I was able to follow the guide on how to setup my dual boot with ubuntu installed first, but I keep running into the same Windows XP install error every time:

"To install Windows XP on the partition you selected, setup must write some startup files to the following disk:

239367 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP-compatible partition."

I had created a 30 GB partition with gparted on the same hdd that ubuntu is installed on (the 239367 MB partition) and I tried various things to make it work: 1) formatting the partition in FAT32, 2) formatting it in NTFS, 3) Moving the partition intended for windows to the "front" so that it displayed in setup as C:, 4) deleting and re-creating the windows intended partition within the windows setup.  

However, as I had guessed, none of these things fixed my problem, and none of the online dual-boot guides mentioned this little hang up.  I followed all the directions to a T, so I'm not sure what I need to do to fix it...

My Ubuntu partition is using the ext3 file system, and I am currently running 8.04 64-bit version.  The programs that are requiring Windows are Sibelius (music notation software that has known issues in Wine) and the software synthesizer to use with my Edirol PC-80 midi keyboard controller (which also had no success in Wine).  

Sorry for the long post, but I would really like to get this up and running sooner than later, and this forum is always really helpful!!!  Thanks again, and I will look forward to any help and/or suggestions!

---

### Post by upthelum on 2008-05-03
Install windows on VMWare in Linux, saves you using lots of disc space.

---

