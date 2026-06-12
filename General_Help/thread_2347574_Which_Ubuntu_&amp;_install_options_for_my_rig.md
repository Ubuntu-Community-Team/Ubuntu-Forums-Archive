---
title: "Which Ubuntu &amp; install options for my rig ?"
date: 2016-12-26
forum: General Help
---

### Post by oztrailrunner on 2016-12-26
Hi, I am new to the forums & to Ubuntu.
I have a Toshiba P750 Notebook - Intel i5, 64bit, 750gb HDD, 8gb RAM, currently with win10 :(

I am wondering if I should install the 16.10 or the 16.04 verions of Ubuntu on my rig ?

Reading the install process there are some options that I need to select in the "installation type". Should I choose the "LVM" and "erase disk" options ?

Should I be able to have a fully functioning notebook after installing ubuntu, or will I need to install other drivers ?

Thanks

---

### Post by Keith_Helms on 2016-12-26
The Ubuntu releases that come out in April of even numbered years, such as 16.04, are known as LTS releases which stands for Long Term Support.  They are supported for a full 5 years.   Any other Ubuntu releases such as 16.10 are only supported for 9 months.   Unless you have a need for some cutting edge feature, support for brand new hardware or want to help test out interim releases, you should just stick with the 16.04 version.

Unless you want to get rid of Windows, don't select any install options that will erase the disk.  There is usually an option to "install alongside Windows".  You may have to change the size of the Windows partition in order to free up space to install Ubuntu in.  I've been told you should use the Windows tools to resize Windows partitions, so you may need to boot Windows and resize the C: partition as a first step.

Yes, you should have a fully functioning notebook after the install.  Certain wifi chips sometimes have problems and require tweaks after the install.  Depending on what graphics card your laptop has, you may have the choice of using an open source driver or a proprietary driver which, in theory, will give better performance.

---

### Post by oztrailrunner on 2016-12-26
Thanks Keith
Just what I needed to know before pushing the buttons :)
I am not inclined to keep Windows, but perhaps I should do as you suggested and install alongside, then if all goes well with ubuntu then I can get rid of WIN10.

---

### Post by mörgæs on 2016-12-27
Yes, you could try first to install a dual boot but be aware that it's more complicated than a single boot. A dual boot used to be easy but Microsoft is making it increasingly difficult. 

If you encounter problems don't take it as a proof that Ubuntu does not work on your hardware. Could also be that 'pre-installed software' is the cause.

---

