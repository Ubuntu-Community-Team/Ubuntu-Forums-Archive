---
title: "Grub2 Prompt Issue"
date: 2016-11-06
forum: General Help
---

### Post by allinnia on 2016-11-06
So, this is my first post, but I think I need some help on this. I have an Alienware 15 R2 laptop with a 256GB NvME PCIe SSD and a 1.0 TB SATA drive. Windows 10 is installed on the SSD and Ubuntu 16.04 is on the 1TB drive. It was a pain in the @$$ just to get to this point (Wifi, RAID, etc.), but I finally have a working setup. Here's the issue though: After reinstalling Windows on the first drive (since Dell likes to send these machines with RAID instead of ACHI configured), I have left secure boot on and managed to install Ubuntu 16.04. However, I can only access Ubuntu by holding the shift key when restarting windows. Attempting to boot into the "ubuntu" boot option from the BIOS results in landing on the dreaded Grub2 prompt (not the grub rescue prompt). Each of the hd0, gptx systems show "Unknown filesystem" and there is not way to boot from the prompt! I cannot locate the linux kernel or initd image since all the listings show as: unknown filesystem. 

So far, I have reinstalled Grub via the terminal, and restarting works just fine as long as the action is initiated from within Ubuntu. If I do a shutdown, I end up right back at the lovely Grub2 prompt. Again, I can get into Ubuntu using the shift + restart method from Windows, but I would really like to use the Grub boot selection screen to move between the two. I use Ubuntu a lot more than Windows for web development work, but I still need Windows for apps and games etc.

Does anyone have any suggestions?

---

### Post by oldfred on 2016-11-07
I have seen others with similar issues, but do not have a good answer.
Dell/Alienware has been one of the few that did not include description as part of UEFI boot.
Many vendors violate UEFI spec that says not to use description and only valid description is "Windows Boot Manager". But there are work arounds.
It sounds like you are using the edit BCD in Windows work around. I believe that uses UEFI one time boot, where Windows tells UEFI to boot once into something else, which seems to work.
Many dual booters copy shimx64.efi to /EFI/Boot/bootx64.efi in ESP. That is then a fall back or hard drive boot entry. It is the same entry as all external drives/flash drives use.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Oldfred has listed other workarounds in link in signature below and these threads:
       
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789) 

    
       
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

