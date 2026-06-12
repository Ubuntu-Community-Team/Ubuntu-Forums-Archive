---
title: "Change Boot"
date: 2024-04-01
forum: General Help
---

### Post by BNZBKK on 2024-04-01
I have Windows 10 on a small 120GB SSD and Ubuntu 20.22 in a 1 TB HDD which I always use. How do I get it to boot up Windows.

---

### Post by oldfred on 2024-04-01
If both are correctly installed in UEFI boot mode and you have Windows fast startup off(hibernation) then grub should offer to boot Windows.
If not in menu:
sudo update-grub

If not installed in same boot mode, you have to directly boot Windows. If UEFI from UEFI boot menu.
Windows  should not be in old BIOS/MBR boot mode, unless you installed it. Then you have to keep Windows boot loader in MBR.

If update of grub does not work, post link to summary report so we can see exact configuration and make correct suggestions.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by BNZBKK on 2024-04-03
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293556&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293557&stc=1[/IMG]Thank you very much for your response Fred.

I did the 'sudo update-grub' in theTerminal but it did not reveal much. 
I am hesitant to 'Boot Repair' with a USB yet ...do these pics of the BIOS help in the meantime ?

---

### Post by yancek on 2024-04-03
re both these drives internal drives?  Has windows ever booted in your current set up?  It was suggested that you select the Create Bootinfo Summary option which will not make any changes.  If you do that as explained at the site, you will be given a link which you can post here and that should contain enough information for someone to help you.  For users unfamiliar with bootloaders, starting out by doing 'repairs' will often make things worse so don't do that.  Do what was suggested in post 2, quoted below.

> Please copy & paste the pastebin link to the BootInfo summary report  ( do not post report), do not run the auto fix till reviewed 

---

### Post by oldfred on 2024-04-03
Please attach screen shots or photos, not post in line.
You can easily attach with Forum's Go advanced editor & paperclip icon.
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You show an UEFI boot menu, not grub. But it does not show Windows.
And you have boot mode set to Legacy which is BIOS/Legacy/CSM or what Windows used primarily with Windows 7.
Windows 8 or later standard is UEFI with gpt partitioning, but older hardware had both boot modes.
Some older systems did need CSM on, but you still selected UEFI boot.
One of my systems had all the UEFI settings under the CSM/Legacy menu in UEFI settings.
My newer Dell calls it BIOS, but once in "BIOS" it says its is UEFI only. Newer systems do not have old BIOS/CSM/Legacy boot mode at all.

---

### Post by BNZBKK on 2024-04-08
> **oldfred said:**
> If both are correctly installed in UEFI boot mode and you have Windows fast startup off(hibernation) then grub should offer to boot Windows.
If not in menu:
sudo update-grub  .....


This was the result of "sudo update grub"



 z@z-Veriton-X6640G:~$ sudo update-grub
[sudo] password for     .....XXXXXXX
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-26-generic
Found initrd image: /boot/initrd.img-6.5.0-26-generic
Found linux image: /boot/vmlinuz-6.5.0-25-generic
Found initrd image: /boot/initrd.img-6.5.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Ubuntu 22.04.3 LTS (22.04) on /dev/sdb6
Adding boot menu entry for UEFI Firmware Settings ...
done
z@z-Veriton-X6640G:~$

---

### Post by oldfred on 2024-04-08
Windows not shown.
Can you directly boot Windows from UEFI boot menu. Same menu you use to choose boot of USB flash drive installer.
Lets see all the details of your configuration:.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2024-04-08
There isn't much any one here can do to help you due to your hesitation to provide information needed, the output of bootrepair.  Are both the drives you refer to internal drives?  Did your windows 10 ever boot successfully on the computer in question?  Have you checked the drive on which you have windows to see if it is healthy? Have you checked connections on the drive?  Are you able to use if for anything?

It is generally recommended that you install your systems in the same mode (UEFI or LEGACY/CSM) particularly if they are on the same physical drive.  This is not your case.  I know from personal experience (accidentally acquired) that a Legacy install of Ubuntu will boot an EFI install of windows on a different physical drive.

---

### Post by BNZBKK on 2024-04-09
> **yancek said:**
> There isn't much any one here can do to help you due to your hesitation to provide information needed, the output of bootrepair.  Are both the drives you refer to internal drives?  Did your windows 10 ever boot successfully on the computer in question?  Have you checked the drive on which you have windows to see if it is healthy? Have you checked connections on the drive?  Are you able to use if for anything?

It is generally recommended that you install your systems in the same mode (UEFI or LEGACY/CSM) particularly if they are on the same physical drive.  This is not your case.  I know from personal experience (accidentally acquired) that a Legacy install of Ubuntu will boot an EFI install of windows on a different physical drive.

 > **yancek said:**
> Are both the drives you refer to internal drives?

Yes, internal.
    
> **yancek said:**
> Did your windows 10 ever boot successfully on the computer in question?

No.


> **yancek said:**
> Have you checked the drive on which you have windows to see if it is healthy?

Can't check it if I can't see it.



> **yancek said:**
> Are you able to use if for anything?

I'm using it for this.

---

### Post by BNZBKK on 2024-04-09
> **oldfred said:**
> Windows not shown.
Can you directly boot Windows from UEFI boot menu. Same menu you use to choose boot of USB flash drive installer.
Lets see all the details of your configuration:.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

 

[QUOTE=oldfred]
Can you directly boot Windows from UEFI boot menu. Same menu you use to choose boot of USB flash drive installer.
Lets see all the details of your configuration:.[/QUOTE]

No Windows is not displayed anywhere !


Once again, thanks for your attention Fred but this is too complex however, I'll install the new 22.04 next month and see if I can rescue or even 'see' Windows then. 
It probably has to do with partitioning and any suggestions would be welcomed


Sincerely.
BNZ

---

### Post by yancek on 2024-04-09
If you have windows 10 on this SSD I would expect you would have some proprietary windows software you created, like a recovery CD/DVD/USB.  You should be able to download software to use to troubleshoot windows or repair the bootloader on windows if that is the problem.  Since it never booted on the current machine, did it boot on an earlier machine or how did you come in possession of it?

If you have Linux (Ubuntu) installed on one drive and booting from that drive, it will boot a windows install from another physical drive even if not in the same boot mode.  That is my experience.  Without more information, the most likely scenario is corrupted or missing boot files on the windows drive.  That can't be fixed from Linux only using tools designed specifically for windows.

---

