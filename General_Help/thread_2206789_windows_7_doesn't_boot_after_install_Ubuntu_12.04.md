---
title: "windows 7 doesn't boot after install Ubuntu 12.04"
date: 2014-02-20
forum: General Help
---

### Post by evaristo-yoka on 2014-02-20
My laptop has a 500GB sata disk, I made three partition on the disc and installed windows 7, then I installed ubuntu 12.04 and it say the next:

If you do not have this disc, contact your system administrator or computer...

file: \Boot\BCD
status: 0xc000000e
info: An error occurred while attempting to read the boot configuration.

I made a usb bootable, and try to repair windows but it says that is not the same version, then I try to install it, and says that i can not be installed on a GPT partition.

Then I used the boot repair, and this is the URL [http://paste.ubuntu.com/6967895/](http://paste.ubuntu.com/6967895/)

I Hope you can help me. 
Greetings

---

### Post by oldfred on 2014-02-20
You have a drive partitioned as gpt.
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can boot with either BIOS or UEFI from gpt partitioned drives.
And both Ubuntu and Windows only boot from MBR(msdos) partitioned drives with BIOS.

It does not look like you installed Windows in UEFI mode.
And you have Ubuntu in BIOS boot mode, with grub installed to the protective MBR of the gpt drive.
You also have grub in the partition boot sector of the FAT32 partition that would be the efi partition. But grub2/Ubuntu in UEFI mode installs efi boot files into partition, not a BIOS type boot into the PBR or partition boot sector. You almost never install grub to a PBR. And Windows PBRs have to have Windows boot code.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

 Convert Windows BIOS to UEFI - Also command line install of files to efi partition
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by matthew-zimmer on 2014-02-26
I'm having a similar issue although I'm not attempting to dual-boot.

My laptop (Acer Aspire V5) came with Windows 8 pre-installed and the UEFI. I removed Windows and installed Ubuntu 12.04.4 but my partitioning went awry (unintentional, I always use one root and one swap and that's it) and I ended up with two tiny 1MB unallocated sectors at the front and end of the disk. I'm gathering this has something to do with GPT confusing the partitioner. Anyway, I decided to use the Windows recovery pendrive I created to load the command prompt and convert the GPT to MBR via diskpart and clean the disk. It worked and I then installed Ubuntu 12.04.4 over the whole of the drive.

Unfortunately after it restarted I was unable to boot into anything, receiving the "no bootable device" error message. Ubuntu fully installed but the UEFI was wiped out and broke the Grub, I think...

Luckily for me I've got Ubuntu 13.10 on DVD so I switched over to Legacy boot mode in the BIOS and installed 13.10 and it worked, I successfully booted into Ubuntu however upon checking my partition tables one of those pesky 1MB unallocated sectors reappeared at the end of the disk.

My swap partition is at the end next to and in front of this 1MB unallocated space, is it safe to use Gparted from the LiveCD to extend the swap over this tiny area? Is that even possible? I'm going to try in about 5 minutes anyway.  :)

Have I done something totally crazy here?

I've never encountered these little 1MB unallocated sectors on any other machine and I'm worried I may have done something bad to the system by wiping out the UEFI.

Thanks for taking the time to read this, I'm a noob.

*** EDIT: I went ahead and resized the swap partition with Gparted and absorbed that little 1MB and everything appears to have worked, I now only show two partitions on my drive, one root and one swap (as I like it) and they're both MBR. I'd still like advice on how to prevent this fiasco from happening in the future, like when 14.04 comes out. I don't think this was a normal experience and I'm worried I should be using the UEFI with GPT instead of the Legacy BIOS and MBR because everything I've read indicates UEFI is better, faster, etc. Thanks though, this is all very interesting!

---

### Post by oldfred on 2014-02-26
With gpt partitioning you do have to have an efi partition to boot in UEFI mode and have to have a 1 or 2MB unformatted partition flagged as bios_grub.

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

    
While the old CHS had some gaps between partitions, the new 4K rounding has slightly larger gaps between partitions to make sure they are compatible with the new 4K and SSD type drives. The larger gaps now may show in gparted as they may be over 1MB rounded where old ones were just under 1MB and not shown.

With the new very large drives, it often is better not to just have one very large / (root) partition. Drive heads then have to jump all over drive to find boot files which with Linux formatting may be anywhere in partition. Often better to have a 20 or 25GB / partition and separate /home or data partition(s).

If drive will be used as UEFI in future also better to use gpt and create an efi partition at beginning of drive as it can be difficult to reformat later if it has lots of data. The efi partition should be first or at least near the beginning of the drive. If in BIOS mode with gpt then you have to have the bios_grub partition. You can have both on a drive, but one one or the other is used depending on how you boot.

---

