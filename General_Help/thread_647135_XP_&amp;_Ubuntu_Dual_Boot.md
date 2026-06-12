---
title: "XP &amp; Ubuntu Dual Boot"
date: 2007-12-22
forum: General Help
---

### Post by pepperwood on 2007-12-22
Presently have an older PC set up to run a dual boot OS consisting of XP & Linux on separate HD's.

This will be considered a new boot job, I guess you'd call it. One HD will be for XP and the other devoted to Debian & Ubuntu EMC. Just a newbie at this and will have to be walked through the procedure.

So far have been able to install & boot XP on the Master HDD using NTFS File system. May not need FAT32 but has been suggested that some Linux Distros don't do well with NTFS.  Is it possible & how do you partition the Windows HD for both NTFS & Fat file systems? I will be using a CD to install Windows XP.

Debian & Ubuntu EMC on the Slave HD will be installed on the Secondary HDD.  I gather that the Secondary HDD will have to be partioned for each distro but haven't the foggiest on what commands & how to set them up  or where to look for them to use or partions to set for. Have CDs for each to install. Thinking of installing Debian EMC first & then Ubuntu EMC or vise versa just to compliment each other. 

Finally upon bootup/startup is there a special file that needs to be installed someplace and where in order to be able to choice which OS to startup with?

Your assistance concerning this matter would be very much appreciated. Just an old senior newbie when it comes to Linux but I think you folks will be able to help. Thank you!

---

### Post by pyronaut on 2007-12-22
its pretty simple actually. Install windows and then get the Live Cd for ubuntu. It will show you all the drives etc. just reformat the slaves to ext2 or ext3 with your required partions and then install. It should automagically set up the boot manger for you etc..... installation si a breeze now ... try the latest flavor of ubuntu

---

