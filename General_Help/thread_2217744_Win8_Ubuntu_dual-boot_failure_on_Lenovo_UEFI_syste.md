---
title: "Win8 Ubuntu dual-boot failure on Lenovo UEFI system"
date: 2014-04-18
forum: General Help
---

### Post by hans12345 on 2014-04-18
I am trying to install Ubuntu (in this case 13.10 since I made the DVD before 14.04 was ready) on a friends Lenovo H520. The goal is to have a dual boot system.

The Lenovo had Win 8.1 installed with probably an AMI style BIOS. It has the full UEFI, secure boot etc. I note that there have been problems with some Lenovo PCs, but do not know if the H520 is included in these problem machines.

We followed the instructions on:
   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

We disabled secure boot and all its friends. We used the Intel Ubuntu image of 13.10. (This appears to be a 32/64 bit image)  

I believe Ubuntu 13.10 is now installed. It appeared to be OK just after the installation. But not on reboot.

If the BIOS is left in Legacy boot mode, the PC will not boot. If put in Secure mode, it will only boot to Win 8. 

When we get to the part of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which tells us to use boot.repair, we followed those instructions. This ended with us being told to get the 64 bit version, so we downloaded a CD version from:
    [http://sourceforge.net/projects/boot-repair-cd/?source=directory](http://sourceforge.net/projects/boot-repair-cd/?source=directory)

This version runs and ends with a message "you have installed on sda10 a Linux version that is not EFI compatible ..." and stops.

The boot-repair makes a detailed log on the paste bin at :
   [http://paste.ubuntu.com/7269676/](http://paste.ubuntu.com/7269676/)


Thanks for you help!

---

### Post by oldfred on 2014-04-18
There is no combined 32bit/64bit version. And with any newer computer you should only download the 64 bit version. Actually any computer that need the 32 bit version probably needs Lubuntu as full Ubuntu with Unity needs more RAM and better video that an old 32 bit processor cannot support.

Do not use any auto reinstall options. Many are reporting that the auto reinstall option may say replace Ubuntu (but does not mention Windows) and then erases entire hard drive.
I think it is Windows is hibernated or has chkdsk flag set, but it could be an installer bug.

Also best while Windows works to make a Windows repair flash drive and a full image backup of Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

If you turn secure boot off, and turn on Legacy/BIOS/CSM mode or UEFI off, Ubuntu should boot as it has grub in the protective MBR of the gpt drive. You then can only boot Windows by turning UEFI back on, or turning off BIOS boot mode. But you may still have video mode settings that are required to get it to boot.

Best if both Ubuntu & Windows are UEFI boot. And only 64 bit is UEFI capable.  I would now download 14.04 as it has many improvements for newer hardware.

Often vendors UEFI is similar across models. So some settings these users had to do may apply. But newer 14.04 may not need all of them.

 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)

---

### Post by hans12345 on 2014-04-19
Thanks Oldfred for your detailed reply. 

ATM I cannot work on the PC since it is at my friend's home and it's Easter holidays.

Meanwhile I'll work through the given references (some of which I already know) and report when my friend returns.

:P

---

### Post by hans12345 on 2014-05-15
A report on my latest steps.

The Lenovo H520 has Win 8 pre-installed and he has no installation disk. I note that there have been problems with some Lenovo PCs, but I see the H520 is compatible. ([http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop](http://www.ubuntu.com/certification/desktop/make/Lenovo/?page=5&category=Desktop&category=Laptop)). One key aspect is that the Lenovo has a GPT not an MBR. 

We reran the complete installation process again, carefully checking for variants we could have missed.

We disabled all the Smart boot and friends.

We wanted to try booting from the DVD in UEFI mode but this is not allowed in the BIOS.

So, in the BIOS we enabled CMS (compatibility mode) and disabled 'auto' (which would still have us booting into Win 8) and set CMS to 'legacy boot'

Ubuntu seemed to install correctly, but on reboot, we got the message saying there was no boot disk available. If the BIOS is left in Legacy boot mode, the PC will not boot. If put in Secure mode, it will only boot to Win 8. 

We ran the boot repair disk from [http://sourceforge.net/projects/boot-repair-cd/?source=directory](http://sourceforge.net/projects/boot-repair-cd/?source=directory)

Whatever we tried with boot repair, we got the same result:

"You have installed on sda10 a Linux version which is not EFI-compatible. It is probably incompatible with your computer. Please install an EFI-compatible system. For example, Linux-Secure-Remix-64bit and Ubuntu-64bit are EFI-compatible systems"

We reported this problem to the boot repair email some weeks back, but no answer yet.

The obvious question is can we somehow boot Ubuntu in UEFI mode? Would a USB be better than a DVD? (I see little chance in the BIOS)

Or can we convert a 'non-UEFI' Ubuntu (installed via legacy) into a UEFI installed Ubuntu?

(Please note, I have started new threads with new related questions at: 
[http://ubuntuforums.org/showthread.php?t=2224214](http://ubuntuforums.org/showthread.php?t=2224214) and
[http://ubuntuforums.org/showthread.php?t=2224213](http://ubuntuforums.org/showthread.php?t=2224213))

Your help very much appreciated

---

### Post by coffeecat on 2014-05-15
> **hans12345 said:**
> (Please note, I have started new threads with new related questions at: 
[http://ubuntuforums.org/showthread.php?t=2224214](http://ubuntuforums.org/showthread.php?t=2224214) and
[http://ubuntuforums.org/showthread.php?t=2224213](http://ubuntuforums.org/showthread.php?t=2224213))


This thread closed.

---

### Post by bapoumba on 2014-07-11
Reopened as requested here : [http://ubuntuforums.org/showthread.php?t=2233956](http://ubuntuforums.org/showthread.php?t=2233956)
Spin offs closed.

---

### Post by oldfred on 2014-07-11
Not sure where you are at now.
May be best to run a new BootInfo report from Boot-Repair and post link.

But only the 64 bit version of Ubuntu is UEFI capable. 
Only if you have drive partitioned with gpt partitions will UEFI correctly install.
If you installed 32 bit it will be BIOS only and drive will be usually MBR(msdos). 
But Ubuntu can boot in BIOS mode from a gpt partitioned drive, so with new systems gpt is better.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Even if Ubuntu is BIOS boot and Windows UEFI boot, you can dual boot just not from grub menu. You should be able to select from UEFI menu either Windows or Ubuntu. Some switch auto automatically from BIOS to UEFI if setting is UEFI & BIOS. Others may require you to turn on UEFI to boot Windows and turn on Legacy/BIOS/CSM mode to boot Ubuntu. You may also be able to use one time boot key often f12 but varies by vendor.

---

### Post by hans12345 on 2014-07-11
Summary of where we are now

I am trying to install Ubuntu 14.04 on a friend's Lenovo H520 which has Win 8 pre-installed and he has no installation disk. The goal is to have a dual boot system. Since he lives some 20 miles away, I only get there once every 3-4 weeks, so progress is slow. I have 4 Ubuntu PCs (all non UEFI) myself, 2 of which are dual boot, so I have some experience.

The Lenovo had Win 8 installed with the full UEFI, secure boot etc. I note that there have been problems with some Lenovo PCs, but have checked and it appears that the H520 is not one of these problem machines. ([http://www.ubuntu.com/certification/hardware/201305-13634/](http://www.ubuntu.com/certification/hardware/201305-13634/)). However, the certification does look a little less than 100%: "Standard images of Ubuntu may not work at all on the system or may not work well ..."

It is clear that it would be best if both Ubuntu & Windows are booted in UEFI mode. But the H520 will not boot in UEFI mode from CD or USB. So, in the UEFI (what we used to call BIOS) screen, we disabled secure boot and all its friends and enabled CMS (compatibility mode) and disabled 'auto' (which would still have us booting into Win 8) and set CMS to 'legacy boot'

We followed the instructions on:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

We ran the complete installation process twice, carefully checking for variants we could have missed.

Ubuntu seemed to install correctly, but on the requested reboot, we got the error message 1962  saying there was no boot disk available. In the Lenovo's Discussion Community there are lots of complaints about this 1962 error, but it seems it is a general error message and not relevant to Ubuntu.  If the BIOS is left in Legacy boot mode, the PC will not boot. If put in Secure mode, it will only boot to Win 8. 

We ran the boot repair disk (64 bit version) from [http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

Whatever we tried with boot repair, we got the same result:
"You have installed on sda10 a Linux version which is not EFI-compatible. It is probably incompatible with your computer. Please install an EFI-compatible system. For example, Linux-Secure-Remix-64bit and Ubuntu-64bit are EFI-compatible systems"

The boot-repair makes a detailed log which can be seen on the paste bin at :
[http://paste.ubuntu.com/7269676/](http://paste.ubuntu.com/7269676/)
We reported this problem to the supplied boot repair email in April, but no answer yet.

I believe Ubuntu 14.04 is now installed. The installation seems to be OK and in Gparted it looks good. But it will not boot.  Nor is there any sign of GRUB (with purple or black background)

Possible ways to progress:
- can we convert a 'non-UEFI' Ubuntu (installed via legacy) into a UEFI installed Ubuntu?
- would a 2nd hard disk allow us to install Ubuntu more easily? It would certainly allow us more freedom for experimenting without risking the Win 8 installation. I note that “Boot-Repair can convert a BIOS install to UEFI if you used gpt partitioning on the second drive and Ubuntu is on second drive.” (Thanks OldFred)
- are there safe steps we can take by using a Live Ubuntu CD and trying terminal based work? I like to avoid terminal use since it is easier to get things wrong but maybe this is what we need to try. There are some hints at:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1302939](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1302939)
but I have not tried them since this is not a dual boot question.

Please advise if I should post extra information. But it will not appear for a couple of weeks, until my next visit...

---

### Post by oldfred on 2014-07-11
If Boot-Repair says it is not compatible it is because you used the 32 bit verion. Only the 64 bit version is UEFI capable. You will have to reinstall. But see caution in link in my signature.

If 64 bit Ubuntu on gpt partitioned disk and you have an efi partition (from Windows) then Boot-Repair can convert install to UEFI boot. Only one efi partition per hard drive.

---

### Post by hans12345 on 2014-08-19
> **oldfred said:**
> If Boot-Repair says it is not compatible it is because you used the 32 bit verion. Only the 64 bit version is UEFI capable. You will have to reinstall. But see caution in link in my signature.



Thanks OldFred

The Lenovo H520 is an Intel i3 64-bit PC.

I see on Ubuntu the  14.04.1 downloads page:

[COLOR="#006400"]Desktop image
Ubuntu is distributed on four types of images described below.

The desktop image allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of image is what most people will want to use. You will need at least 384MiB of RAM to install from this image.
There are two images available, each for a different type of computer:
PC (Intel x86) desktop image
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
64-bit PC (AMD64) desktop image
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead. [/COLOR]

I have used the first one. Surely this is for 64-bit Intel CPUs?

---

### Post by oldfred on 2014-08-19
No, Intel x86 is the 32 bit version.
Your i3 chip is Intel 64 bit or what used to be EM64T Intel type. 


       uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit

      
 The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. 
They will not work on Intel Itanium Processors (formerly IA-64).
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

We are just about to the point that you do not need the 32 bit version of full Ubuntu with Unity ever. There are a few very unique applications that still have not been recompiled for 64 bit, but very few. Those may be exceptions. And to make a few systems Windows only, they are installing 32 bit UEFI on a 64 bit chip. And certain Intel Atom chips were 32 bit only or only had 32 bit support chips on motherboard.

And full Ubuntu has Unity which takes a somewhat newer video chip or card and those are only in systems that are 64 bit and usually more RAM. It really is intended for newer systems.

Then if system is 64 bit but light on RAM and video processing power Xubuntu or Lubuntu are better choices. 
Or if really 32 bit then Lubuntu or if real short of RAM other very lightweight Linux, but those are usually very old computers.

---

### Post by hans12345 on 2014-08-21
Wow!

I'm used to wasting time with Microsoft, but I do expect better from Ubuntu. The download page is horribly confusing.

Thanks OldFred.

---

