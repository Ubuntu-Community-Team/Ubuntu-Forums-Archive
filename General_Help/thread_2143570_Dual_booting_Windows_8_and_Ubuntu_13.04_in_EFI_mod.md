---
title: "Dual booting Windows 8 and Ubuntu 13.04 in EFI mode"
date: 2013-05-09
forum: General Help
---

### Post by jerden on 2013-05-09
I bought a new laptop with Windows 8 installed and installed Ubuntu alongside it in EFI mode. Grub 2 shows up with Ubuntu listed in it but no Windows partition. When I use Gparted the partition is still there but not showing up on boot. I have run the boot-repair program but that hasn't fixed the problem. Is there anywhere I can add it into Grub to view it and boot into it?

Thanks.

---

### Post by oldfred on 2013-05-09
Post the link to BootInfo report from Boot-Repair.

Is your system one that will boot Windows with secure boot off, or does Windows only boot with secure boot on. Also some are modified to only boot the Windows efi file. Boot-Repair has a work-around for those also.
Did you install Ubuntu in UEFI mode or BIOS mode. How you boot installer is how it installs.
Did you install the 64 bit version?
Is this an UltraBook? Also has issues on RAID and dual video.

---

### Post by dannyvanderzande on 2013-05-09
I've got this same problem.
I bought a win8 laptop this morning and succesfully uefi installed Ubuntu 13.04 x64.
Upon rebooting there are 2 Windows items in grub but open trying them I get the error that the file isn't found.
I made sure I didnt format my windows partitions, and I found my EPS partition at gpt0,2
What can I do to fix it?

edit: I had to re-enable secure boot te get windows to work.. solved for me!

---

### Post by jerden on 2013-05-10
> **oldfred said:**
> Post the link to BootInfo report from Boot-Repair.

Is your system one that will boot Windows with secure boot off, or does Windows only boot with secure boot on. Also some are modified to only boot the Windows efi file. Boot-Repair has a work-around for those also.
Did you install Ubuntu in UEFI mode or BIOS mode. How you boot installer is how it installs.
Did you install the 64 bit version?
Is this an UltraBook? Also has issues on RAID and dual video.

Boot repair: [http://paste.ubuntu.com/5610712/](http://paste.ubuntu.com/5610712/)

I have secure boot turned off at the moment and when I turn it on all I get on the screen is "System Boot Failed, Operating system is invalid" With it turned off I get the Grub window and Ubunut boots fine.

I installed Ubuntu 64bit in UEFI mode.

This is an Ultrabook, Sony Vaio Duo 11 (SVD112290S). No RAID involved and dual video works perfect. It outputs over VGA and HDMI at the same time with ease. I'm using a Core i7-3687U 8GB Memory and 256B SSD.

---

### Post by oldfred on 2013-05-10
You did format over the Windows partition. Your efi partition only has the Windows efi boot files and of course they do not work as there is no Windows.
With secure boot off can you select ubuntu from UEFI menu and get it to boot? If not you have a system that violates UEFI spec (as do lot of Windows) and internal modified UEFI to only boot the Windows efi boot file even with secure boot of. 
If Ubuntu does not boot directly you can rename Winows boot file to really be the grub efi file to make it work. 

But if you did not intend to overwrite Windows you may need to restore that first. It looks like you overwrote all partitions except the efi partition, so you do not have the vendor recovery partition. Did you make a full backup before installing? If not you have to contact Vendor and get a new DVD. Some may only charge a shipping fee, other charge for a full install.

---

### Post by jerden on 2013-05-10
> **oldfred said:**
> You did format over the Windows partition. Your efi partition only has the Windows efi boot files and of course they do not work as there is no Windows.
With secure boot off can you select ubuntu from UEFI menu and get it to boot? If not you have a system that violates UEFI spec (as do lot of Windows) and internal modified UEFI to only boot the Windows efi boot file even with secure boot of. 
If Ubuntu does not boot directly you can rename Winows boot file to really be the grub efi file to make it work. 

But if you did not intend to overwrite Windows you may need to restore that first. It looks like you overwrote all partitions except the efi partition, so you do not have the vendor recovery partition. Did you make a full backup before installing? If not you have to contact Vendor and get a new DVD. Some may only charge a shipping fee, other charge for a full install.

When I turn the laptop on in UEFI mode Ubuntu boots up no problem. The grub even has a selection for Sony's built in recovery system that works fine. It allows me to boot into the BIOS etc. If I reinstall windows onto a NTFS Partition could I use an Ubuntu live CD with boot repair to get them both back up and running?

---

### Post by jerden on 2013-05-10
Just as a quick run down I used parted and it shows the Windows partition. Did it just get removed from the EFI partition?

(parted) print                                                            
Model: ATA TOSHIBA THNSNS25 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  183GB   183GB   ext4
 5      183GB   205GB   21.5GB  ntfs
 4      205GB   248GB   42.9GB  ntfs
 3      248GB   256GB   8463MB  linux-swap(v1)

(parted)

---

### Post by oldfred on 2013-05-10
Is your pastebin not correct? It only shows this. Post a new link.

>  Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       194,559       192,512 EFI System partition
/dev/sda2         194,560   483,588,095   483,393,536 Data partition (Windows/Linux)
/dev/sda3     483,588,096   500,117,503    16,529,408 Swap partition (Linux)



---

### Post by jerden on 2013-05-10
Ok I'll run the Boot-repair program again and send you the new read out.

---

### Post by jerden on 2013-05-10
[http://paste.ubuntu.com/5652196/](http://paste.ubuntu.com/5652196/)

The 21GB partition is just a storage partition I'm using so that both OS's can access the same files if they need to.

---

### Post by oldfred on 2013-05-10
You did overwrite some Windows partitions. You have to leave those as essential for Windows. You will probably just have to delete swap and make that the Windows system reserved again or just make swap a bit smaller as the Windows system reserved is not large.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by jerden on 2013-05-14
> **oldfred said:**
> You did overwrite some Windows partitions. You have to leave those as essential for Windows. You will probably just have to delete swap and make that the Windows system reserved again or just make swap a bit smaller as the Windows system reserved is not large.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

I will shrink the SWAP partition then and see where I can go from there.

---

### Post by jerden on 2013-06-13
> **jerden said:**
> I will shrink the SWAP partition then and see where I can go from there.

Ok sorry for the delay, work interfered with life :p I resized a partition and called it MSR but it looks like it isn't used. After I used it I booted up my Windows 8 CD and clicked repair, it repaired the boot file I guess and my laptop then would only boot into Windows. I then ran the Ubunutu live image and ran boot repair but it gave me back the same GRUB as last time with no Windows boot entry in the box. Windows is working and so is Ubunutu I just not together.

Here is a new Boot Repair output:

[http://paste.ubuntu.com/5761696/](http://paste.ubuntu.com/5761696/)

---

### Post by oldfred on 2013-06-13
Did you turn fast boot off in Windows? That is hibernation and Linux NTFS driver will not normally mount a NTFS system that is hibernated to prevent damage.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

