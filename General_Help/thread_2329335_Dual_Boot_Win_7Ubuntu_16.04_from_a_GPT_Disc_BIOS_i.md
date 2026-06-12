---
title: "Dual Boot Win 7/Ubuntu 16.04 from a GPT Disc BIOS in Legacy Mode"
date: 2016-06-30
forum: General Help
---

### Post by DAVID_LECKIE on 2016-06-30
Sorry if this is a bit long but it’s a complicated story.

I had a working quad boot system. (Win 7 Ult 64 bit, Win 7 Pro 32 bit, XP and Ubuntu 15.04)
(The two versions of Win 7 was for software testing)

The HDD was a MBR disc.  Everything worked and I was happy!
Then there was a M/B fault that was beyond economic repair. Fortunately everything was fully backed up with Paragon B & R 11.
My copies of Win 7 were genuine MAPS versions so transferable to a new machine.

I bought a new Acer Travel Mate P253.
This had a 500GB GPT disc but booted in Legacy Mode.  I reinstalled my backup of Win 7 Ult, used the original install disc to get it booting and sorted out new drivers etc and had a working machine again. 
By this time I did not need Win 32bit and XP for backward compatibility so I did not install them.
I installed my backup of Ubuntu but it refused to boot from the re-installed backup.

Disc space was getting short so last week I bought a new 1TB WD Blue drive.
This turned out to be an MBR disc (strange I thought by 2016 this was no longer used)

Anyway I reinstalled my backup of Win 7 Ult and it refused to boot.   The install disc could not sort the problem. (A backup from a GPT disc going onto a MBR disc)

I used DISKPART to convert it to a GPT Disc, reinstalled my backup, used the install disc to sort the boot and I had a working system. I like to keep my OS’s and Data on separate partitions.

I also created 3 Linux partitions Root (Ex4), Home (Ex4) and Swap.
See below there are 8 Primary Partitions so UEFI Legacy is not MBR
I am a bit puzzled as to why there are 2 GPT System Partitions.

[IMG]https://c2.staticflickr.com/8/7429/27382949594_97de634dd6_b.jpg[/IMG]


I then installed Ubuntu 16.04 64 bit (fresh install).
I was really worried about where to install Grub 2 so I put it dev/sda7 my root partition (Local Disc F above) 
Rebooted no sign of my Grub loader it just booted to Win 7 as normal.

Tried EasyBCD 2.3 (The UEFI “aware” version I realise “aware” does not mean compatible)
I am in Legacy mode. I now gather UEFI Legacy is NOT the same as MBR booting.
However it says the following with a GPT disc and BIOS in legacy mode.

[IMG]https://c2.staticflickr.com/8/7782/27382582473_bfdb9e3efb_o.jpg[/IMG]

I now changed my BIOS Boot Mode to UEFI
Bingo! I get the Grub 2 Bootloader menu as I wanted and Ubuntu 16.04 boots perfectly BUT there is  no option to Boot Win 7.

Not really what I wanted! I can now either Boot to Windows 7 or to Ubuntu but I have to change the BIOS settings each time.
I have had years of experience with MBR booting and understand it. I am also slowly starting to understand full UEFI but this UEFI Legacy mode has me beaten.  I just don’t understand how it works.

When I install Ubuntu I choose “Something else” option.

OK on reading the Grub2/Installing Wiki it says on Page 2 “Device for bootloader installation”
I selected dev/sda7 my root partition.
Should I have chosen dev/sda? But then where does the bootloader go?
(I was worried about messing up the Win 7 boot so did not choose the ab ove option.)

What I want is a normal dual boot with a menu to select.  I am not bothered if it’s a MS Windows menu or a Grub menu so long as I get the option to dual boot.  
I don’t want to have to alter my BIOS settings each time I change OS.

---

### Post by yancek on 2016-06-30
If you are using UEFI, then you need both systems, windows and Ubuntu installed UEFI and you should have a separate EFI partition on the drive with files for both windows and Ubuntu on that partition.  The first step is to check to see if you have that partition.  An explanation of this process is at the site below:

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My understanding is that if you have GPT partitions with windows you need to use UEFI.  If you are not able to resolve this, go to the site below and download and run 'boot repair' from Ubuntu.  Select the option to Create BootInfo Summary and post a link to the output here and someone with a little expertise in UEFI should be able to help.  Do NOT try to make any repairs!

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2016-06-30
All versions of Window since XP only boot in UEFI mode from gpt partitioned drives and only in BIOS boot mode from MBR drives. Or you cannot boot a BIOS/MBR install of Windows from gpt.

The Windows 7 installer on DVD is BIOS only. But it can be copied to a flash drive and some files moved around to create /EFI/Boot/bootx64.efi which is the default UEFI boot device.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html
       [/URL]  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html) 
    
 Convert Windows 7 install to UEFI
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI) 

[URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]
[/URL]

---

### Post by DAVID_LECKIE on 2016-06-30
Hi 
Thanks for the quick reply.
My 1st problem relates to *"you should have a separate EFI partition on the drive with files for  both windows and Ubuntu on that partition.  The first step is to check  to see if you have that partition*."

For some (unknown) reason I have not **one** but** two **such partitions.  
The Wiki says "*It is strongly recommended to have only 1 ESP per disk.*"
I need to get rid of one the question is "which one?" 
If I get rid of the wrong one will I will "break" my boot?


Yes my disc is GPT but it is currently booting Win 7 in "Legacy mode".
The Wiki is quite clear on this  
"What is important is below:  
[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 

[*]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

Windows 7 is installed in Legacy mode.
I installed Ubuntu in Legacy mode but when I boot I don't get the Grub menu it just boots straight into Win 7 with no choice.
However if I select UEFI mode it boots into Ubuntu with no Win 7 option.

Totally confused.

Dave

---

### Post by DAVID_LECKIE on 2016-06-30
Hi thanks for the quick reply.

*"All versions of Window since XP only boot in UEFI mode from gpt  partitioned drives and only in BIOS boot mode from MBR drives. Or you  cannot boot a BIOS/MBR install of Windows from gp*t."

My drive is GPT partitioned but its booting in "Legacy Mode".



"[I]The Windows 7 installer on DVD is BIOS only."
[/I]It seems to also work fine in UFEI Legacy Mode. 



[I]"But it can be copied to a  flash drive and some files moved around to create /EFI/Boot/bootx64.efi  which is the default UEFI boot device."
[/I]
Yes this would be a good option but the process seems quite complicated.I will need to carefully read the Wiki before doing this.

Off to do some further reading

Thanks

Dave

---

### Post by oldfred on 2016-06-30
UEFI legacy mode AKA CSM is BIOS emulation.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode.

Ubuntu can boot from gpt with either UEFI if you have ESP or CSM if you have a bios_grub partition.
But Windows will not boot in BIOS mode from gpt.

Not sure but the one link seems to discuss conversion of a Windows 7 BIOS install to UEFI boot. As posted above:

 Convert Windows 7 install to UEFI
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736) 


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

