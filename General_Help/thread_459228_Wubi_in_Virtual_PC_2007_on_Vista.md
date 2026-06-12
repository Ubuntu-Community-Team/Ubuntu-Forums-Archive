---
title: "Wubi in Virtual PC 2007 on Vista"
date: 2007-05-30
forum: General Help
---

### Post by bobb32756 on 2007-05-30
I want to install Wubi on my Virtual PC 2007 running on Vista Ultimate.  I need to put the 
Wubi-7.04-test2.exe on a CD but I need to make it bootable.  I am new to Linux and I 
need the correct files to add to the CD to make it bootable.  Can anyone help with what 
or where to find the files I'll need to add to the CD to operate in Virtual PC 2007.

---

### Post by ecology2007 on 2007-05-30
Wubi is designed especially to eliminate the need of having to use a CD, or having to test linux in Virtual PC, VmWare or Virtual Box.

You will be able to download, install and run Ubuntu side by side with Windows only by running wubi.exe.
(No need to put it in Virtual PC, no need to burn a CD)

Is Vista running in Virtual box, or is Virtual PC running in Vista ?
Why do you want a CD ?
Do you have access to the internet on this computer ?


Give us as many details as you can think of and a clear scheme of what you want to do.

---

### Post by bobb32756 on 2007-05-30
I am running Vista Ultimate x64 as my OS.  I have Virtual PC 2007 installed that I am running Win XP & Win 2K on for doing my tech support for work.  I was wanting to install the Wubi on the Virtual PC 2007 so I can work with it when I'm not on calls for support.  In order to install it into the Virtual PC 2007 it has to come from CD or Floppy.  To get the CD to start or be recognized it has to be bootable for the installation.  If I have the system files, I can make the CD bootable when I burn it.  My computer is dual boot with XP 64 bit and Vista.  I am running my home network on broadband so I do have high speed internet.  The only reason I was trying to do it on my Virtual PC so I can work with it while having my Vista and other OS's active for work.  This is my first attempt at learning Linux.

---

### Post by ago on 2007-05-31
You can run wubi from within XP that you have in virtual PC. But it's probably better to use a dedicated ubuntu image for that, or simply create an empty virtual disk, boot the virtual PC from the live CD and install that into the virtual disk.

---

### Post by matt_heys on 2007-05-31
From what I have read, it sounds like you would be better off downloading the default live cd, booting a blank Virtual PC off the CD and installing from there.

Like other people have said Wubi is designed for people who do not want/know how to repartition and install Linux with Lilo or Grub and just want to try it without getting some virtulization software.

I have Ubuntu installed in a VMWare machine so I can mess about whilst at work, then I have also installed it with Wubi so I can mess further with better performance then a virtulization platform.

---

### Post by Computer Guru on 2007-05-31
Or install Ubuntu as a real OS with Wubi, then install VMware or Xen on Ubuntu and put XP & 2k in there like I did :)

---

### Post by bobb32756 on 2007-06-02
Thank you for those responses. They were very helpfull. Before I started to think about the Wubi, I had tried the install of Ubuntu x64 7.04 and the 32 bit version. I had to run Ubuntu in the safe graphics mode to install. Otherwise the display was unreadable. When the display came up I couldn't do anything with it. I will try again to install the Ubuntu 7.04 from the disc.  Thanks again for your input.

---

### Post by minhmeoke on 2007-06-02
Do you have a widescreen display? If so, you may need to edit the xorg.conf file to match your screen resolution; see [http://ubuntuforums.org/showthread.php?t=457109]("http://ubuntuforums.org/showthread.php?t=457109"); and substitute the appropriate screen resolution values for your display.

---

### Post by bobb32756 on 2007-06-02
I'm running dual 19" LCD monitors with total screen resolution of 2560 X 1024.  Both are full screen instead of widescreen.

---

