---
title: "No boot loader, boot repair failed?"
date: 2014-09-15
forum: General Help
---

### Post by fernand2 on 2014-09-15
Hello ,


i was wondering if you can help me with my laptop. After installing Ubuntu i didn't get a grub bootloader display, but instead my laptop started directly into windows 8.1 .


After some reseach, i found out that i had to use boot repair in order to fix this. So i did. Buth the problem is still there. 


I tried the boot repair in UEFI mode with secure booth ON and with leagcy mode (secure booth of and in CMS mode.) As a result i received the following two URL's; 


UEFI mode : [http://paste.ubuntu.com/8346310/](http://paste.ubuntu.com/8346310/)
[COLOR=#000000][FONT=Tahoma]lagacy mode : [http://paste.ubuntu.com/8349242/](http://paste.ubuntu.com/8349242/)[/FONT][/COLOR]  


I hope you can help me 


p.s. i am using version 12.04.05 LTS, and my laptop : Toschiba satelite came with windows 8.1 pre-installed

---

### Post by oldfred on 2014-09-15
If your system is Windows 8.1, you may have better results with 14.04. While 12.04.5 has many of the UEFI updates, 14.04 is still more current.

Is your UEFI/BIOS updated to the most current version from vendor?

Your Windows install is UEFI, so only boot using UEFI. Make sure fast boot is off and usually better to have secure boot off.

If you do reinstall Ubuntu only use Something Else and make sure you have fully backed up Windows and efi partition before you do that. There is a major bug in the auto install options that may say they overwrite Ubuntu but erase entire drive. 
       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

    
I thought Toshibas just worked ok with Ubuntu. 
Can you use f12 and choose the ubuntu entry?
Can you in your UEFI change boot order to make ubuntu entry first?

I see Boot-Repair is offering this, if you said yes undo it for now:
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

---

### Post by grahammechanical on 2014-09-15
I see this

> grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 1.99-21ubuntu3.16,grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 1.
GRUB too old [COLOR=#AA22FF]**for **[/COLOR]SecureBoot.

That is why Ubuntu 14.04.1 is better. It has Grub 2.0 not 1.99

And I see this

> Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file! Please disable SecureBoot in the BIOS.

have you and are you doing that?

Regards.

---

### Post by fernand2 on 2014-09-15
thanks for the respons oldfred :) I would have loved to use 14.04 but for a project i wil be needing 12.04 :S
as respons to your sugestions/questions: 

-  Yes my sytem has the last updated of the bios/UEFI.
-  "[COLOR=#000000]Your Windows install is UEFI, so only boot using UEFI. Make sure fast boot is off and usually better to have secure boot off." <-- done that, didnt work :S[/COLOR]
-  I did the instal as the reinstall with the something else function. 

-when i press F12 ubuntu isn't shown. this is the same in UEFI.

-"[COLOR=#000000]buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)" <-- didnt do this, i wanted to reserve this as a last resort.. dont realy undestand what it will do actualy ...

thanks for the link, i will check it out later :)

I hope you can help me resolve my problem, thanks :)

[/COLOR]with kind regards,
Fernand

---

### Post by fernand2 on 2014-09-15
HI [COLOR=#000000][FONT=arial]grahammechanical , thanks for your response :)
because of a project i will be needing 12.04 :S so i cant solve the problem by installing 14.04
for your second notion : i tried to boot in uefi mode with secureboot enabled as disabled, buth i couldnt select the given "efi file"/boot option.

with kind regards,
Fernand [/FONT][/COLOR]

---

### Post by oldfred on 2014-09-15
What brand/model system?
What video chip?

The Boot-Repair rename is/was for those systems (HP & Sony maybe others) that modify UEFI to only boot Windows. It renames the Windows efi file and puts a copy of grub into the Windows folder and renames it to be the Windows file name. System then thinks it will boot Windows, but really boots grub. But then you can only boot Windows from grub menu as UEFI entry for Windows is grub. And later when Windows updates the Windows efi file it overwrites the grub version and you have to redo the rename. There are now several other work arounds that work and typically work better as you have fewer issues.

You can try a work around. Most seem to use the rename of bootx64.efi to really be grub. Or use rEFInd.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Other Toshiba, you may have similar type issues.
 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

[URL="http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789"]
[/URL]

---

### Post by fernand2 on 2014-09-16
Hi oldfred, today i wanted to post my laptops specs. However i noticed in dxdiag that the bios version wasn't the same as the update i had presumed to have taken.
So i went to toshiba support and got me the new bios/UEFI. installed it and checked if there where any changes towards the problem. but there weren't . So i tought lets run boot repair again. Only this time it did work. :)

The only problem now is that i run into the purple screen when booting ubuntu. however Win 8.1 does still function.

Thanks for the support so far :)

just in case you where wondering.
I have a Toshiba sattelite L-50-A-19PSSK6E.
12MB RAM , i7-4700MQ CPU 2.4GHZ
Intel HD Graphics 4600
NVidea GeForce GT 740M

---

### Post by oldfred on 2014-09-16
Are you booting with Intel Video or nVidia in control. Can you set that in UEFI settings or is it one that auto switches?

If booting with nVidia you need nomodeset. But if Intel you need one of several Intel options that may work.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by fernand2 on 2014-09-16
So far as i can tell, it's booting on intel video and i don't see any function to switch it either ,in the bios/UEFI.

this is what i get when i press e in the grub :
> setparams 'Ubuntu, with Linux 3.13.0-35-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='(hd0,gpt6)'
search --no-floppy --fs-uuid --set=root {id x} "some serial, dont know if critical but wil keep it a secret for now"
linux /boot/vmlinuz-3.13.0-35-generic.efi.signed root=UUID={id x} ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.13.0-35-generic

i tried nomodeset after $vt_handoff but didnt work, also tried to replace "quiet splash $vt_handoff" with nomodeset, but didnt work either.

I also noticed one thing, at the first boot i got a grub menu when secureboot was still on, but after starting windows to check if it was still working, i got a warning about a signature wasn't present.
As a result the laptop didnt "start" and i had to turn secure boot off.

---

### Post by oldfred on 2014-09-16
If booting with Intel then nomodeset usually does not work and you have to use one of the Intel boot parameters.

---

### Post by fernand2 on 2014-09-17
Hi oldfred,

i tried with the intel adjustments. but it didnt work :S 
After having tried it, i tought lets try boot-repair again. As a result i could get in ubuntu with secure mode on.
but after the first session i got the same problem again. 

With secure mode on:
"Boot failure : a proper digital signature was not found. One of the files on the selected boot device was rejected by the secure Boot feauture"
with secure mode off: 
purple screen

Do you know a possible sollution ? do i need to install something from ubuntu live cd? or change a file / setting in the bios/UEFI ?

with kind regards,
Fernand

btw. at the install, the combination of uefi and safe mode on resulted in a grey screen when tying to start ubuntu from a DVD.

---

### Post by oldfred on 2014-09-17
If you did not install the secure boot version of Ubuntu kernels & grub then secure boot will not work. But usually Boot-Repair upgrades you to include the secure boot versions.
But usually best just to leave secure boot off anyway. There is/was? a bug in grub that you cannot boot 8.1 from grub menu with secure boot on, only using one time boot key or directly from UEFI menu.

When you say secure boot off, you still want UEFI on, not CSM/BIOS/Legacy or whatever your system calls the old way to boot.
Purple screen sounds like BIOS mode, but may just be a video driver issue. 
Have you tried booting with recovery mode or second entry in grub menu?

---

### Post by fernand2 on 2014-09-17
hi,

>  [COLOR=#000000]There is/was? a bug in grub that you cannot boot 8.1 from grub menu with secure boot on, only using one time boot key or directly from UEFI menu.[/COLOR]
 yes this indeed one of the problems. after boot-repair i have got a 1 time change to start ubuntu or windows 8.1 . After this change i wont be able to start either with secure mode on

yes, i have tried to boot in recovery mode (with secure mode off) but this resulted in a purple or black screen (it did difer from time to time)

I have installed ubuntu with secure mode on in uefi, but just in case is there a way to install the [COLOR=#000000]secure boot version of Ubuntu kernels & grub afterwards ?

[/COLOR]with kind regards , F

---

### Post by oldfred on 2014-09-17
Some other possibly similar model Toshiba and the issues they had.

 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

I gather even with Toshiba you have to rename bootx64.efi and boot hard drive. UEFI wants to only boot Windows.

If you can boot or resolve video issues:
      
 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by fernand2 on 2014-09-18
Hi  oldfred,

I don't now what happend, but today everything started to work.
Thanks for the support :)

with kind regards,
Fernand

---

### Post by oldfred on 2014-09-18
Glad it is working.

I think it is the sprinkling of "Magic Dust" that is the fix that worked. :)

---

