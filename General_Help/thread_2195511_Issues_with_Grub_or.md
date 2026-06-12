---
title: "Issues with Grub or ?"
date: 2013-12-24
forum: General Help
---

### Post by de Bacon on 2013-12-24
I have multiple HDDs in my system with multiple linux OSs.  The other day I decided to try a distro called KXStudio.  Upon completion of the install I discovered detrimental changes not to the partition I installed on, but to a different partition wi my old default OS UbuntuStudio OS on it.  It seems to have reverted everything that changed (software updates, changes to the "Home" file system, Desktop Settings, etc., to sometime in January 2013. 

I am thinking that it has somehow reverted to one of those way down the list, Grub files that could be opted to.  

In grub 1.99 it shows only two options for this sdb partition, rather than what I assume to be the list from each major system update that is  utilized.  Actually I don't know what generates that list.

Does anyone know how to revert this back to what it used to be, something that can bring my old system back to its former state?

Thanks

edit-
Also, the new OS does not function, won't boot up, through grub.  At this time, I don't care about this problem

---

### Post by oldfred on 2013-12-24
Are you attempting to share /home or another other system partition?

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by de Bacon on 2013-12-24
Thanks oldfred,

No I am not attempting to share folders or anything else, if I understand the question.

I have a couple issues that I need to understand before proceeding.  

First is that I am unsure that I'll be able to connect  to the web from a live disc.  This is because my ISP switched their method of connection, now requiring PPPoE set-up to connect.  If I had a router this would not be an issue but I have no need for a router.  I have not yet attempted to connect with the Ubuntu-Studio live disc, though the KXStudio doesn't have the drivers included to allow PPPoE.  Maybe the Ubuntu-Studio has it and maybe it doesn't.  I'll see when I get that far.  

The other issue is If I can't get connected through PPPoE due to no drivers, how can I run the boot-repair software?  I can download it now but don't know how I could properly access  and run the package from a live disc?  That is the same  issue as the PPPoE setup files if they are not included in the live disc.  I have the PPPoE package in a tarball package but it I can't access or run it form a live disc, it does no good.

I may let this lay for the remainder of the day??? then still I might not.  

Thanks again for the input.

:)

---

### Post by oldfred on 2013-12-24
I do not know about PPPoE, but did find this which is older.

[https://help.ubuntu.com/10.04/installation-guide/sparc/pppoe.html](https://help.ubuntu.com/10.04/installation-guide/sparc/pppoe.html)

A bit newer
[https://help.ubuntu.com/12.04/installation-guide/powerpc/pppoe.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/pppoe.html)

---

### Post by de Bacon on 2013-12-25
Thanks again oldfred,

I don't know too many things and believe I may have made an error in running a system update on this OS yesterday.  I have not completed it by rebooting the system, due to the unknowns that remain.  It may be perfectly okay to do that, but I also think that it could make the changes final, a scenario I'd like to avoid.  Ignorance, as blissful as it is said to be, leaves so much potential for doing harm. 
 
After your previous posts, I have done some study of the documents you've contributed, printing their content for use if I gain enough confidence through understanding to proceed.  Right now I am trying to figure out the how, the where and what it means, to follow the instruction from that document on PPPoE ([https://help.ubuntu.com/12.04/instal...rpc/pppoe.html](https://help.ubuntu.com/12.04/instal...rpc/pppoe.html)) where it states, "Boot the installer with the boot parameter modules=ppp-udeb."  I don't know where or what to insert to fulfill this requirement.  I see no syntax with this statement, nor how to get to a boot installer. This may be referring to the live .iso file, but I don't know that. Furthermore, I don't recall ever seeing a prompt when an .iso file begins to run or elsewhere in its startup.  With the above stated lack of confidence I am still reluctant to proceed.  

At this point I am thinking I should isolate the HDD that this messed up OS is on to avoid any potential conflicts that may come from the other HDDs and or from Grub1.99.  Yet in an attempt to do that early yesterday, it failed to boot with a 'no such device.....' error message. I then plugged all the HDDs back in and booted.  It was sometime after that event when I thought to do an update (system security issues), leaving me with the unknowns which prevent my will to reboot immediately to carry on.  I know that there is little lost if I continue with the update (reboot), and rebuild the system as I want it, although it is a lot of unwanted toil.  

Thanks for your assistance.  
Carry on

---

### Post by oldfred on 2013-12-25
All boot parameters are added to the end of the Linux line with grub or added with f6 when booting installer in BIOS mode.

This shows both the famous 'any' key & f7 BIOS and further down the grub screen. With UEFI or once installed it is always the grub screen. You use e for edit on grub menu scroll down to linux line and replace quiet splash with boot options. You use the manual edit line for testing different boot options, but once you find those that work you can permanent add them in a grub file to be always included. I like to remove quiet splash when testing just to see boot process. It also is logged so you can review later if need be.

Use your boot option inside or if you have nVidia in addition to nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by fantab on 2013-12-25
> **de Bacon said:**
> I have multiple HDDs in my system with multiple linux OSs.  The other day I decided to try a distro called KXStudio.  Upon completion of the install I discovered detrimental changes not to the partition I installed on, but to a different partition wi my old default OS UbuntuStudio OS on it.  It seems to have reverted everything that changed (software updates, changes to the "Home" file system, Desktop Settings, etc., to sometime in January 2013. 

I am thinking that it has somehow reverted to one of those way down the list, Grub files that could be opted to.  

In grub 1.99 it shows only two options for this sdb partition, rather than what I assume to be the list from each major system update that is  utilized.  Actually I don't know what generates that list.

Does anyone know how to revert this back to what it used to be, something that can bring my old system back to its former state?

Thanks

edit-
Also, the new OS does not function, won't boot up, through grub.  At this time, I don't care about this problem

I think the KXStudio installation didn't complete. By default Grub always, AFAIK, installs to the first HDD, ie /dev/sda.
If you had your 'default' OS and its grub on /dev/sda then those grub fles have been overwritten by the new Grub, but the installation failed as well to install Grub files properly to its native partition.
Hence an unbootable system.

Since the original grub files seem to have been overwritten, it is your only easy option to re-install GRUB from the 'default Studio'. Just the 'default' UbuntuStudio's Live DVD/USB and follow the directions below:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

You don't need web connectivity using the above.

---

### Post by de Bacon on 2013-12-25
Thanks a bunch for your help! :)  I think I lost my mind somewhere along the line!  All is well again, the KXStudio works too!

---

