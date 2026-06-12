---
title: "UEFI ; Ubuntu doesnt see my windows partition when installing."
date: 2014-10-29
forum: General Help
---

### Post by pizzalover1974 on 2014-10-29
Ubuntu doesnt see my Windows 7 partition when installing. Im guessing its something to do with Bill Gates and pals new attempt to mess with Linux by pretending UEFI is about protecting bootloader when its more about preventing Linux from dual boot installing.

I unfortunately got asus motherboard on ebay uk with UEFI (malware) bios. Tried turning it off and it still tries to boot into windows 7 before looking for my DVD and installing Ubuntu. Even then if I force DVD to load first, and Ubuntu installer loads, it cant see my Windows partition. 

Have I somehow enabled UEFI mode when installing Windows 7 while I was still connected to the internet via Ethernet cable? Would I be better to re-install Windows 7 (with the hrs of coma inducing misery that entails)?

"Something else" Ubuntu partitioning option is too complicated for me...im an average joe kind of user with poor terminal skills. 

Setting up partitions manually kind of has me going "um..whuh?". Im not totally retarded..I do build my own PCs. But thats easy like Lego for PC. This UEFI crap is making me consider hunting down a new NON UEFI motherboard for AM3+.

Is Ubuntu gonna ubdate its install process so UEFI and dual booting fixes itself auto again...like the old non EUFI bootloaders?

Luckily I have 2 PC's, so can use Ubuntu on my Media center (with Linux only install). But Would like it on my Gaming PC in dual boot mode.

PS: The reason I wont pure install my Gaming PC, is bacause I still need windows for Legacy gaming of older non Linux titles and new ones I occassionally buy without Linux support (though I do try to buy mostly Multi OS games that include Linux support now).

---

### Post by LinuXXuniL on 2014-10-29
Hey

It will work eventually, just try to follow steps described in the documentation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Good Luck!

---

### Post by sudodus on 2014-10-29
Is this correct?

1. You  build your own PC

2. You install Window 7 (you do it yourself, you did not buy it pre-installed)

Then I think you should be able to switch off UEFI (run CSM or whatever it might be called, when you emulate old style BIOS). I know some systems might not have that option, but most of them have. Anyway it is worth searching for it, because if you find it, dual boot will be easy (as it used to be).

Otherwise we might need help from *oldfred* ...

---

### Post by ajgreeny on 2014-10-29
Admittedly I do not have the dual boot situation that causes the problems for some users, but I do not think you need to fear UEFI or call it malware; it is just a new form of the now old, legacy BIOS, which does have many drawbacks.  UEFI works fine for many people, including me, with 3 new computers running in UEFI mode with no problems at all. UEFI is fine, in my opinion, it is just different from the old BIOS version.

Some computer manufacturers, not necessarily Microsoft, have made life more difficult by stopping anything but the Windows efi files from booting, meaning you have to rename the ubuntu efi files in /boot/efi before booting.
See [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win) for the details of this, though you probably will not have that problem..

---

### Post by yancek on 2014-10-29
UEFI is a newer method of booting computers.  It was actually started by Intel and other manufacturers.  The link below to an Intel site has all the information you would want and probably more than you want to read about UEFI.  There are 11 manufacturers represented on their board of directors which does not include microsoft.  The Secure Boot feature is just one part that was added to enable windows systems to try to boot with it in a secure fashion.

[https://software.intel.com/en-us/articles/uefi-introduction](https://software.intel.com/en-us/articles/uefi-introduction)

---

### Post by oldfred on 2014-10-29
I just build a new system with a Asus AR motherboard. And it was just as bad as what many have posted on complicated installs with pre-installed Windows.

I had lots of UEFI settings to change. The first was Windows or other. I guess Windows setting really should say secure boot, but Asus seem to think only Windows uses secure boot.
Then for whatever reason all the other UEFI settings can only be accessed in the CSM setting. And even selecting UEFI and CSM, UEFI first would not boot Ubuntu flash drive in UEFI mode, only BIOS. When I set it to UEFI only then I could boot in UEFI mode.

---

### Post by rbmorse on 2014-10-29
The Windows 7 installer doesn't use EFI mode by default. Unless you explicitly select the UEFI installer at boot (and it's sorta hidden) WIN7  installed in conventional BIOS mode. In any case the problem (Ubuntu doesn't see my windows partition when installing) doesn't sound like an EFI related issue, anyway (although I'm not totally sure by what he means by "installer doesn't see").

---

### Post by pizzalover1974 on 2014-10-29
Well Im gonna reinstall Win 7 to be sure...**** backwards...Been told its possible Ubuntu first then Win 7...see if that resolves it...Turned off secure boot and UEFI in Bios. But was still bootloading Windows and when force loading DVD to load Ubuntu ...Ubuntu wasnt seeing my Win 7 Partition to do an automatic dual install option.

Anyway im gonna do a total reinstall **** backwards and hope that fixes the OS's seeing each other on my hard drive with a UEFI motherboard. When I can be arsed to do the slow and boring Win reinstall.

---

### Post by rbmorse on 2014-10-29
When you say you couldn't see your Windows 7 partition...what were you expecting to see? What installer option were you using? 

Whoever told you it was possible to set up a dual-boot machine installing Linux first may be technically correct at some level of proficiency with both Linux and Windows bootloaders, but he/she certainly wasn't doing you any favors.

---

### Post by oldfred on 2014-10-29
With Both Ubuntu & Windows you have to be consistent on how you install. Either both UEFI or both CSM/BIOS.

And Windows 7 DVD normally installs in BIOS mode and will convert a gpt partitioned drive to MBR. But it does not do it correctly and leaves gpt backup partition table. Then Linux tools see both gpt & MBR(msdos) and fail as they do not know which you really want or have. 

You can install Windows 7 in UEFI mode, but have to convert to flash drive and make some minor updates.

If drive is gpt Ubuntu will install in either BIOS mode or UEFI boot mode. But then how drive is partitioned will determine if Windows installer will work. 
Windows only boots in UEFI mode from gpt partitioned drives.
Windows & Ubuntu only boot in BIOS mode from MBR partitioned drives.

And how you boot installer for both Windows & Ubuntu is how it will want to install, but if partitioning is not correct you will have issues.

---

### Post by pizzalover1974 on 2014-10-30
"Windows only boots in UEFI mode from gpt partitioned drives."

So i'm assuming then I install Linux first MBR partition mode....leave a fat partition space (using qparted or some other partitioner) by sliding the big partition to leave a large empty space. Then installing Win 7 in that fat empty partition while not enabling the hidden UEFI mode in the install, also while connected to the web? Keeping it off secure boot mode.

As im assuming the Linux first install will be best to partition the drive as a MBR partition. And that a MBR partitioning is Microsoft system?I can set partition mode in Ubuntu installer to partition MBR style? Ive already turned of UEFI on mobo and also turned of secure boot.

So as to get this to work with both Windows 7 and Linux on an annoying mobo? I dont want to buy a flash drive for Win 7 (not chucking out a 2TB hard drive) so UEFI all round isnt an option. So i'm guessing MBR is an option in Ubuntu and wont default to UEFI? Will I need to force Ubuntu to use MBR? 

And that doing it Linux first will force my annoying Mobo to load Linux then allow me to install windows on top?

PS: I do it Windows first normally, but as newish ASUS my board sees the Windows partition and trys to preload that ahead of my DVD drive no matter how I set it in Bios. Linux then cant see the Win partition after a forced boot of DVD to install. Im assuming I have to try the hard backwards option to trick my motherboard into letting Linux in.

---

### Post by sudodus on 2014-10-30
I would set the computer mode to BIOS alias CSM, and boot from the install DVD/USB drive and use ***gparted*** to repartition the drive (create an MSDOS partition table), and after that install Windows 7 and after that Ubuntu. Then things should work without further tweaking.

It is possible to install Windows after Ubuntu, but Windows will overwrite the boot loader, so you will have to boot from the install DVD/USB drive and ***re-install a grub bootloader afterwards***, and after that boot into Ubuntu and run ```
sudo update-grub
``` to give you the boot options (Ubuntu and Windows) in the grub menu. I think all these operations are more difficult in UEFI (than in BIOS alias CSM), and you may need 'Boot Repair' or some manual tweaking. But it is possible.

---

### Post by pizzalover1974 on 2014-10-30
Ok I will try normal way around with the UEFI and secure boot option off in bios..and make sure I dont do anything weird in windows install. Then try Ubuntu..if that fails its the hard way..Thanks for the Information. :)

---

### Post by oldfred on 2014-10-30
There are some advantages to gpt & UEFI.

If drive is something over 1.2TB and empty, the Ubuntu installer will use gpt partitioning, even for BIOS boot mode. But gpt is only required if drive is over 2TB as MBR was designed when the first PC hard drive came out in the 1980's and TB was not heard of.
But if drive is gpt Windows will only install & work in UEFI.

Windows in BIOS mode will only install to MBR partitioned drive to a NTFS formatted partition with the boot flag. If drive is blank it will use two primary partitions, one 100MB boot partition so you can encrypt main install. Boot partition not otherwise required. If UEFI it has several required partitions and order on drive is critical, so best to always install Windows first if you do not know details of required partitions.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


> [h=3]Advantages of GPT[/h] 
[LIST=1]
[*] Uses GUIDs (UUIDs) to identify partition types - No collisions.
[*] Provides a unique disk GUID and unique partition GUID for each  partition - A good filesystem-independent way of referencing partitions  and disks.
[*] Arbitrary number of partitions - depends on space allocated for the  partition table - No need for extended and logical partitions. By  default the GPT table contains space for defining 128 partitions.  However if the user wants to define more partitions, he/she can allocate  more space to the partition table (currently only gdisk is known to  support this feature).
[*] Uses 64-bit LBA for storing Sector numbers - maximum addressable disk size is 2 [ZiB]("http://en.wikipedia.org/wiki/ZiB").
[*] Stores a backup header and partition table at the end of the disk that aids in recovery in case the primary ones are damaged.
[*] CRC32 checksums to detect errors and corruption of the header and partition table.
[/LIST]
 [h=3][/h]

---

### Post by pizzalover1974 on 2014-10-30
Well I fixed dual booting issue with UEFI board...had to switch off UEFi, Secure boot and reinstall windows.

WIndows wouldnt let me remove the partitions..first was GPT second was MBR. So I force loaded Ubuntu to install over it by selecting dvd boot option. Then used that install to kill the Windows 7 partition. That finally made my UEFI motherboard say UEFI was off, must be a board glitch.then I killed my Ubuntu partition be reinstalling windows in non UEFI mode on top...
Then I fked up got my disks confused and accidently installed Zorin linux in dual boot with WIN 7...:lolflag:

Oh well..I still have Ubuntu on my media PC for my TV. I will fix the Zorin install tommorrow maybe. My brain is dead. Need sleep.

*update* Have installed Ubuntu now im awake and found the correct disk..Zorin didnt look like I could get it off with out messing with partitioning or doing those installs from scratch again..so kept Zorin on it own newly resized 250gb partition along with 450gb windows 7 and 1300 gb Ubuntu install..My HDD is huge 2 TB one so it can afford it.

---

### Post by sudodus on 2014-10-31
Congratulations :KS

Now you know how to do it. The next time you want to install a dual boot or multi boot system you will know how to do it. And thanks for sharing :-)

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by oldfred on 2014-10-31
Glad you got it working. 

I suggest that you keep smaller system partitions and have large shared data partition(s). When using XP I had a NTFS shared data partition and the Linux shared data partition. 
With the shared data partitions, you can have the same email, bookmarks, photos and files in all systems. You do have to install the same app like Firefox, Thunderbird in eachsystem to use the shared profile's data.

---

