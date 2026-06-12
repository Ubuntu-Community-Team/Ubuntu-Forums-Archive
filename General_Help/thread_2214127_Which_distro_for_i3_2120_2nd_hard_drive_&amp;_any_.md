---
title: "Which distro for i3 2120 2nd hard drive &amp; any issues?"
date: 2014-03-30
forum: General Help
---

### Post by Ace..... on 2014-03-30
My son accidentally deleted 12.04 from his hard drive, creating a boot error which has now been fixed:
[http://ubuntuforums.org/showthread.php?t=2212372](http://ubuntuforums.org/showthread.php?t=2212372)
 
There remains the swap file on the drive, but I believe it can be deleted and re-formatted.
However, he has installed a 2nd 500Gb hard drive.

It occurred to me that we could install an Ubuntu version on the 2nd drive, leaving win7 on the first.
This would put ubuntu on the new drive in order to spread the risk, in case of drive failure.

Where are we on current thinking for an O/s suitable for an i3 2120 with 8Gb ram?
Are there any issues to watch out for doing a 2nd hard drive installation?

---

### Post by westie457 on 2014-03-30
This thread is close enough in principle for what you are asking.

[http://ubuntuforums.org/showthread.php?t=2211941](http://ubuntuforums.org/showthread.php?t=2211941)

---

### Post by grahammechanical on 2014-03-30
If the CPU is 64bit then install a 64bit operating system. I am a Ubuntu user. Do not expect me to recommend another operating system.

It is certainly possible to install Ubuntu on a second hard drive. I have done it. You have to decide which drive is going to have boot priority. It should be the drive with Ubuntu on because the Windows boot loader will not give us an option to load Ubuntu but the Ubuntu boot loader (Grub) will give us an option to load Windows.

So, if Ubuntu is going on the second drive (sdb) then you must choose the Something Else option and direct Ubuntu to install into sdb. Make sure that Grub is going to be installed into the MBR of sdb. If Grub installs into the MBR of sda it will over-write the windows boot loader.

So, if you set the boot priority to sda then Windows will load. If you set the boot priority to sdb then Grub will load and offer Ubuntu and Windows as choices. And if something happens to Ubuntu or to Grub, then you can still load Windows by changing the boot priority in the BIOS.

Regards.

---

### Post by Ace..... on 2014-03-30
Thanks grahammechanical..... that was exactly the sort of information I was looking for. :p

@ Westie457 I think you're right, there may well be some help in that thread applicable to me. :p

---

### Post by Ace..... on 2014-04-02
It didn't go well.

On first boot I got a warning of poor graphical performance, and chose the option to 'run on low graphics just this once'.
At the OK (statement left [OK] right) I got just 2 OK's) I believe it stated 'pipe broken...... it then stalled.
I tried again choosing reconfig graphics, and got a few more statements before it stalled again.

Here's what I did:

I decided on 12.04 64bit Ubuntu., using the original disk that I'd created for the first install last year.
I have around 100 blank CD's, so was going to try Xubuntu 13.x but after the long download, it failed to fit on a cd.
I guess I should have gone for the alternate mix -  **BTW Is it the same as desktop, but without the ability to install within windows?**

Anyway I was happy with 12.04, and the install went as expected, with **the graphical install presentation displaying as I believe it should**.


[LIST=1]
[*]The PC did not boot directly (after the install) into ubuntu.
I missed the boot config - Asus has a strange bios that doesn't provide a full list of 'move up/down' boot options, one clicks an alternate boot config and it exits directly to it - in this case grub on the 2nd disk. However, in getting to grips with that, it booted into windows.
I state this in case Ubuntu needed to be loaded immediately after its install.
[*]I had slimmed down the ntfs drive during install to create space for ubuntu, and inserted / for mount location.
[*]As the PC had booted to windows, I slimmed the ntfs a little more and added a small partition for a windows swap file (to take advantage of the 2nd disk).
This didn't change the start location of ubuntu as that partition was un-touched.
(looking back I know I should have done this later, but time was short and the PC was needed urgently for a project).
[*]The primary disk still had its original ubuntu swap partition.
[*]The graphics were a problem in that I had to remove the geoforce 550 graphics card so I could connect to the VGA output of the motherboard, but as stated above, the install graphics displayed fine.
[*]The graphics memory allocated on the motherboard was 64Mb.
Should this have been higher - did I lower the allocation on original PC setup due to it not being needed..... I can't say for certain, but I may have done (but the install graphics were fine).
[/LIST]

All the above, are the elements that I can think of that were 'a little off standard', other than Ubuntu was being installed on a second drive.
Grub listing appeared as predicted, with win7 as a boot option.

Interesting fail. :(

---

### Post by oldfred on 2014-04-03
Post link to BootInfo report.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

With nVidia you have to use nomodeset on install and first boot or until you install nVidia proprietary graphics. I just installed 14.04 in another partition and forgot the nomodeset and it just locked up with black screen like normal. With nomodeset it was low resolution, but once nVidia drive installed and I logged out and back in (not even reboot) it worked with great graphics. I have nVidia 9600GT on a CoreDuo system.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Yellow Pasque on 2014-04-03
> **Ace..... said:**
> Where are we on current thinking for an O/s suitable for an i3 2120 with 8Gb ram?

Whatever OS and/or desktop you want. It's not like you have old hardware that would struggle with latest version of Windows or KDE...

---

### Post by Ace..... on 2014-04-03
@ Temüjin

Thanks for confirming my thoughts on that primary issue.

@ oldfred

> **oldfred said:**
> 
Post link to BootInfo report.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

On this issue, it looks like a straight reproduction of the use of boot-repair, as was the case in thread:
[http://ubuntuforums.org/showthread.php?t=2212372](http://ubuntuforums.org/showthread.php?t=2212372)

However, in that case, there was only one disk with a boot command, and 2 O/S (originally).
We now have 2 disks.
The first boots directly to win7.
There used to be grub, offering a number of boot options, but after my son deleted his ubuntu.... boot-repair rectified the problem (leaving what code.... is that an issue?).

Now we have 2 boot commands.
The first on the primary drive (in the bios) direct to Win7
 
The second on the 2nd drive (in the bios) loading the grub with all options (ubuntu, safe, win7 etc.)

**Can boot-repair examine both disk drives and their boot commands?**
IE. if we load the bootable boot-repair disk.... will it see all the drives, and function correctly?

> **oldfred said:**
> 
With nVidia you have to use nomodeset on install and first boot or until you install nVidia proprietary graphics. I just installed 14.04 in another partition and forgot the nomodeset and it just locked up with black screen like normal. With nomodeset it was low resolution, but once nVidia drive installed and I logged out and back in (not even reboot) it worked with great graphics. I have nVidia 9600GT on a CoreDuo system.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

On this issue of 'nomodeset' I will do more reading (thanks for the links).
However, i did remove the geoforce 550 card, in order to use the basic motherboard vga output (which worked fine during installation)
Let's see what boot-repair comes up with next week, and then we can look at the graphics. :)

---

