---
title: "Need Help with Windows 11 not opening on Dual boot + Kubuntu 24.04"
date: 2024-08-24
forum: General Help
---

### Post by arindam1997007 on 2024-08-24
[LEFT][COLOR=#000000][FONT=&amp]Hi everyone,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]I'm encountering several issues with my dual boot system on a Lenovo Ideapad Gaming 3 laptop running Windows 11 and Kubuntu 24.04. Here are the details:
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]**Problems:**[/FONT][/COLOR]
[/LEFT]

[LIST=1|INDENT=1]
[*]**GRUB Error:** Selecting Windows from the GRUB menu gives the error: "BIInitializeLibrary failed 0xc0000185." 
[*]**BIOS/UEFI Access Issues:** When trying to access BIOS settings via F1 or F2 keys, or by selecting UEFI firmware settings from the GRUB menu, I get a black screen with only a non-movable cursor visible. 
[*]**USB Boot Failure:** Attempting to boot from a USB with a fresh Windows 11 installation (created using the Windows Media Creation Tool) results in the same error: "BIInitializeLibrary failed 0xc0000185." 
[/LIST]
[LEFT][COLOR=#000000][FONT=&amp]**Steps I've Tried:**[/FONT][/COLOR][/LEFT]

[LIST=1|INDENT=1]
[*]**Updating GRUB:** I ran ```
sudo update-grub
``` from Kubuntu, but it didn't resolve the issue. 
[*]**Boot-Repair:** I used Boot-Repair, went to advanced options, checked "Repair Windows boot files," and applied the changes. Despite the successful message, the problem persists. 
[*]**Disk Checks:**
[LIST=|INDENT=1]
[*]I listed my drives using fdisk -l and verified them with sudo smartctl -a diskname and sudo badblocks -sv disk for all drives. All drives passed the health assessments with no bad blocks found. 
[/LIST]
  
[/LIST]
[LEFT][COLOR=#000000][FONT=&amp]List of my drives:
```
[FONT=monospace][COLOR=#000000]**Device         **[/COLOR][COLOR=#000000]**    Start**[/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000]**  Sectors**[/COLOR][COLOR=#000000]**  Size**[/COLOR][COLOR=#000000]**Type**[/COLOR]
/dev/nvme0n1p1       2048     534527    532480   260M EFI System 
/dev/nvme0n1p2     534528     567295     32768    16M Microsoft reserved 
/dev/nvme0n1p3     567296  327075839 326508544 155.7G Microsoft basic data 
/dev/nvme0n1p4  327077888  810409983 483332096 230.5G Microsoft basic data 
/dev/nvme0n1p5  810409984  810801151    391168   191M EFI System 
/dev/nvme0n1p6  998166528 1000214527   2048000  1000M Windows recovery environment 
/dev/nvme0n1p7  810801152  816658431   5857280   2.8G Linux swap 
/dev/nvme0n1p8  817682432  865488895  47806464  22.8G Linux filesystem 
/dev/nvme0n1p9  865488896  998164479 132675584  63.3G Linux filesystem 
/dev/nvme0n1p10 816658432  817682431   1024000   500M EFI System

[/FONT]
```

I'm out of ideas and unsure about the next steps :(. ChatGPT suggested clearing the CMOS by removing the CMOS battery from the motherboard, but I'm hesitant since I've never opened a laptop before and fear it could lead to more issues.
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Any advice on how to resolve this would be greatly appreciated. Thanks in advance for your help! 
[/FONT][/COLOR][/LEFT]

---

### Post by tea for one on 2024-08-24
You have three EFI partitions /dev/nvme0n1p1, /dev/nvme0n1p5 and /dev/nvme0n1p10
As you can still boot into Kubuntu, do you know which ESP contains the Kubuntu and Microsoft boot folders?

A black screen when trying to access your UEFI settings, that's something to bring to Lenovo's attention.
If you can't boot a Windows repair disk, then it's difficult to repair Windows 11.

---

### Post by arindam1997007 on 2024-08-24
Hi. I don't know which ESP contains the Kubuntu and Microsoft boot folders. Will that help in fixing the issue?

Okay, I shall try to contact Lenovo's customer support if I don't find anything that can solve this.

---

### Post by tea for one on 2024-08-24
> **arindam1997007 said:**
> Hi. I don't know which ESP contains the Kubuntu and Microsoft boot folders. Will that help in fixing the issue?
The original error message "BIInitializeLibrary failed 0xc0000185." indicates that there is something amiss with Microsoft boot files or boot process..
If you knew which ESP contains them, then there is a slim possibility of replacing them when booted into Kubuntu.
Grub will only boot a working Windows.
It's a bit of a longshot because we do not know the exact problem.

It seems to me that your priority is to check the Lenovo forums and Lenovo official support to help you reach the UEFI settings.
The firmware is the responsibility of the vendor and it should always be 100% reliable and accessible.
If this can be resolved, you may be able to boot a Windows repair usb?

---

### Post by oldfred on 2024-08-24
I suspect your first ESP is the Windows original ESP. 
I might try changing esp,boot flags to p1 & see if you can directly boot Windows from UEFI one time boot menu.
That will may break boot of Kubuntu, but once UEFI entry is created to know partuuid of ESP, that it has esp, boot flags may not be required.
UEFI uses GUID/partuuid which actually has been set to very long GUID into the ESP's gpt partition table with esp,boot flags. 
But to be safe be sure to have working live installer to make repairs.

You can see where all the boot files are with Boot-Repair's report.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

In Boot-Repair's advanced mode is the choice to choose where to reinstall grub as auto option not always correct.

---

### Post by tea for one on 2024-08-24
> **arindam1997007 said:**
>  When trying to access BIOS settings via F1 or F2 keys, or by selecting UEFI firmware settings from the GRUB menu, I get a black screen with only a non-movable cursor visible. 
Does the F12 key allow you to access the one-time boot menu?
Do you have a Novo button? [https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad](https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad)

---

### Post by yancek on 2024-08-24
Why don't you just mount partitions 1, 5 and 10 in turn and check to see what is on them.  Do you have a Microsoft directory there?  Do you have an ubuntu directory there?  What's in them.  Or as suggested above, check which EFI has boot and esp flags set.  If all 3 EFI partitions have files, you only need the first one.  If you are not sure, post the contents of each EFI partition here and other members should be able to advise you.

---

### Post by dragonfly41 on 2024-08-24
Another pathway is to install EasyUEFI in Windows 11 and use it during free trial period to inspect EFI from Windows 11 perspective.

Ah. But I see that you cannot boot Windows 11.

Then another option is to use Gparted in Live USB to inspect all three EFI settings.

---

### Post by arindam1997007 on 2024-08-24
> **oldfred said:**
> I suspect your first ESP is the Windows original ESP. 
I might try changing esp,boot flags to p1 & see if you can directly boot Windows from UEFI one time boot menu.
That will may break boot of Kubuntu, but once UEFI entry is created to know partuuid of ESP, that it has esp, boot flags may not be required.
UEFI uses GUID/partuuid which actually has been set to very long GUID into the ESP's gpt partition table with esp,boot flags. 
But to be safe be sure to have working live installer to make repairs.

You can see where all the boot files are with Boot-Repair's report.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

In Boot-Repair's advanced mode is the choice to choose where to reinstall grub as auto option not always correct.

Here is the pastebin link for Bootinfo report : [https://paste.ubuntu.com/p/YWtVb5qQmY/](https://paste.ubuntu.com/p/YWtVb5qQmY/)

> **tea for one said:**
> Does the F12 key allow you to access the one-time boot menu?
Do you have a Novo button? [https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad](https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad)

Yeah I used the Novo button as well. I got option to select BIOS settings, but the same issue is happening -> black screen with a frozen cursor

> **yancek said:**
> Why don't you just mount partitions 1, 5 and 10 in turn and check to see what is on them.  Do you have a Microsoft directory there?  Do you have an ubuntu directory there?  What's in them.  Or as suggested above, check which EFI has boot and esp flags set.  If all 3 EFI partitions have files, you only need the first one.  If you are not sure, post the contents of each EFI partition here and other members should be able to advise you.

Hi. I can see all three of the disk has the flag of boot and esp.

I mounted all 3 EFI partitions, and I could see Microsoft and ubuntu folders being present for partition 1. Microsoft folder is not present in partition 5 and 10. What to do next?

---

### Post by oldfred on 2024-08-24
First reinstall grub. Do not use default as it will reinstall grub to p10.
You may need to update fstab with UUID of p1. See line 278. UUID should be  D635-EA9A for p1 not 79B7-B4EC.
Use Boot-Repair's advanced mode to choose install and ESP.

Your boot entry 0000, see line 117 uses the partUUID of p10. Total grub install will fix that.
The files in p1 then are obsolete, but a reinstall will overwrite then with correct info.
Then you can delete p5 & p10.

Turn off UEFI Secure boot at least for a week.
Updates will soon be released for shim, as Microsoft has obsoleted all of Linux's older versions of shim. 
Short term fix is just to have UEFI Secure Boot off.

On 20th August 2024, Windows released a software patch that revoked shims older than 15.8.
Does not affect Ubuntu only systems.
After August 29th the patch  will be available, sudo apt update && sudo apt upgrade shim-signed. Details:
[https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378](https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378)

---

### Post by tea for one on 2024-08-25
Power on > Tap F12 > PC Boot Menu visible?
Novo button > Boot Menu > Accessible?
Novo button > System Recovery > Anything?

---

