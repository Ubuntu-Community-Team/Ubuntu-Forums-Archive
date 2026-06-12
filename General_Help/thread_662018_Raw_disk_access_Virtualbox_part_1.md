---
title: "Raw disk access: Virtualbox part 1"
date: 2008-01-08
forum: General Help
---

### Post by Elle Stone on 2008-01-08
Part 1, considering the following 2 questions (and a "how to" for question 2, in case anyone wants to try adding a raw access ".vdmk" as a secondary drive for a VirtualBox virtual machine):

Question 1: When reading and writing large (1/2 to 1 gb-sized) files from/to disk, is VMware faster than VirtualBox?  What about for CPU-intensive processing/number-crunching?

Question 2: In VirtualBox, is reading and writing those same large files faster when the disk to/from which they are being written/read a ."vmdk" with raw access, rather than a ".vdi" disk?

My impression (see below) is that providing a VirtualBox virtual machine with raw access to a partition didn't noticeably speed up the read/write process.


Background for questions:

So I made the switch to 64-bit Ubuntu.  My original windows 2000 installation is gone.

I still want to run photoshop cs2, even though my w2k installation is gone.  I routinely work with .psd files in the one-half to one gigabyte size.  My photoshop scratch files tend to be around 2gb in size.  

I got photoshop working pretty well under the latest Wine (9.46 - 9.51), more or less, give or take (slow to start, fonts are not pretty, etc).  But for some reason my nVidia fan spins up whenever I start Wine, and even though the fan stops afer five minutes or so, the noise is annoying.  And my latest wine installation (from source, so probably I did something wrong) is throwing errors that have nothing to do with photoshop.  So exit Wine.  Enter VirtualBox.

Photoshop works even better under the latest VirtualBox windows 2000 guest on Ubuntu host than it did directly under windows 2000.  At least it loads faster (much, much faster) and seems to process things like large-radius gaussian blur at least a little faster, perhaps because my w2k virtual machine has most services shut down and no longer needs to run anti-malware protection, as I don't use it to access the internet anymore.  Also, VirtualBox is undoubtedly taking advantage of its linux underpinnings to make things work more efficiently than plain-jane windows 2000 (the best windows os, in my humble opinion).

But read-write of large files in my w2k vm is just as slow as, or even a bit slower than it was with my original windows 2000 installation.  The cpu pegs at 100% for a long minute or so while the disk IO process reads/writes the large file from/to the disk.  

So on to my questions.

1) VMware or VirtualBox?  I really like VirtualBox.  However, recently I encountered this 7-page review: [http://marsbox.com/blog/reviews/vmware-vs-virtualbox/6/](http://marsbox.com/blog/reviews/vmware-vs-virtualbox/6/) "VMware vs. VirtualBox" dated Tuesday, 01 January 2008.  The author found significantly faster read-write for large (gigabyte-sized) files for VMware, compared to VirtualBox, using the latest version of both vms.  Has anyone tried photoshop under both?  Did either seem faster compared to the other, when swinging large .psd files around, writing to and from the scratch disk, and saving to disk when done?

2) VirtualBox and raw disk access:  The warnings in the VB user manual regarding raw disk access are pretty ominous.  Nonetheless, I gave my w2k virtual machine a secondary drive with raw access to an 8gb dedicated scratch partition on my second physical hard drive (the ubuntu installation and the virtual machines/vdis are all on the first drive).  

HOW TO create a partition with raw access for a VB vm:

Here are the steps I used to give photoshop on a w2k VirtualBox vm a scratch disk with raw access (note: I'm not sure if the ose version can create a vmdk; I'm using the proprietary version).  Bear in mind I am a complete newbie.  Use at your own risk.

i. List the partitions on the drive where the ".vmdk" will go:

~$ sudo VBoxManage internalcommands listpartitions -rawdisk /dev/sdb

gave:

VirtualBox Command Line Management Interface Version 1.5.4
(C) 2005-2007 innotek GmbH
All rights reserved.

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x82  0   /1  /1   364 /254/63          2863           63
2       0x83  365 /0  /1   1023/254/63          7632      5863725
3       0x83  1023/254/63  1023/254/63         60408     21494970

Number 2 is the 8gb scratch partition.


ii. Give myself access to the raw disk:

~$ sudo usermod -a -G disk elle

then log out and log back in and now I'm a member of the disk group.  For some reason "~$ sudo adduser elle disk" didn't do the trick.  I found the "add user to disk group" commands at this website: [http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/) and by following links the author had listed on his tutorial.

iii. Create a ".vmdk" (after reading the manual **very carefully**) to attach to my VirtualBox w2k vm as a scratch disk for photoshop:

~$ sudo VBoxManage internalcommands createrawvmdk -filename /media/vbox/VirtualBox/VDI/scratch.vmdk -rawdisk /dev/sdb -partitions 2 -relative -register

The command above was modelled afer the following two examples: 

from the VBox manual:
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
        -rawdisk /dev/sda -partitions 1,5 -relative -register

from "kilou" on the ubuntu forums ([http://ubuntuforums.org/showthread.php?t=448332):](http://ubuntuforums.org/showthread.php?t=448332):)
VBoxManage internalcommands createrawvmdk -filename /home/kilou/.VirtualBox/WinXP.vmdk -rawdisk /dev/sda


iv. Open VirtualBox gui and under "Details" attach "scratch.vmdk" as Secondary Slave to my w2k vm.  The two choices were "Primary Slave" and "Secondary (IDE 1) Slave".  For real drives, of course you'd use the secondary ide, so as to avoid two drives reading and writing over the same channel.  If I understand how ide works.  Which I probably don't.  Does anyone know whether it makes a difference for virtual machines?  Are there really two ide interfaces to the VB vm, with separate io channels?


v. Start the w2k vm and format the appropriate (second) partition on the new drive that appears when I go to "computer management".  The VB manual says that the "-relative" switch means a normal user rather than root can access the raw drive.  The "-partitions" switch means just the indicated partition actually has raw access.  The other partitions show up in the w2k vm, but the manual says, if I understand it correctly, that you can't actually read or write to them from within the vm.  I didn't try.


vi. Assign the raw disk access partition to photoshop as the scratch disk.



Result: Alas, as far as I could tell, read/write speeds were not noticeably different from running the scratch disk directly on the vm's c-drive or on a regular (no raw access) .vdi added to the vm.  Same painfully slow minute or two with 100% cpu usage to read or write a .75gb psd from/to disk.

So, this is hardly a scientific test.  I'm just an amateur photographer trying to wring maximum performance out of the hardware and software at my disposal.  Anyone experienced in this area, I would love to hear from you.  When running a VirtualBox vm, is disk read/write time noticeably faster with raw access compared to the normal vdi "virtual" access?  Should I recreate my entire w2k virtual machine with raw access, rather than just my scratch disk?  

End of part 1.  Thanks! for reading!  

Part 2 will take up (following "kilou") the question of how to present photoshop (or any other application that needs to read and write large files), running in a VirtualBox windows vm, with a scratch disk that is actually in ram or in ram/swap, using ramfs, tmpfs, or a ramdisk (or ???).

Elle

---

