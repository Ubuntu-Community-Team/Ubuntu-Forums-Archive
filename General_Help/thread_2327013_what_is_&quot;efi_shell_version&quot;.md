---
title: "what is &quot;efi shell version&quot;?"
date: 2016-06-07
forum: General Help
---

### Post by palmgrower on 2016-06-07
Fresh install 16.04. Now pc boots to this screen that reads "efi shell version 2.31. Current running mode 1.1.2 Device mapping table............Should I reinstall 16.04?

---

### Post by ventrical on 2016-06-07
> **palmgrower said:**
> Fresh install 16.04. Now pc boots to this screen that reads "efi shell version 2.31. Current running mode 1.1.2 Device mapping table............Should I reinstall 16.04?

When you are installing Ubuntu on your device you have the option to choose UEFI or BIOS from the CMOS. If you are not able to boot into Ubuntu then you should reinstall or choose the F11 option when booting and choose the reported hdd or usb that you have your install on. Sounds to me like you are booting into the shell by default and that you have to make the manual adjustment in CMOS.

Regards..

---

### Post by palmgrower on 2016-06-07
> **ventrical said:**
> When you are installing Ubuntu on your device you have the option to choose UEFI or BIOS from the CMOS. If you are not able to boot into Ubuntu then you should reinstall or choose the F11 option when booting and choose the reported hdd or usb that you have your install on. Sounds to me like you are booting into the shell by default and that you have to make the manual adjustment in CMOS.

Regards..
1. Please explain how UEFI and BIOS are different. Rather, advise which to choose. Without knowing the difference, I think I chose UEFI.
2. During booting, I hit DELETE to enter BIOS. But it disregards DELETE. I am not sure if I can suceed, but will try F11, and report back.
Thanks.

---

### Post by ventrical on 2016-06-07
> **palmgrower said:**
> 1. Please explain how UEFI and BIOS are different. Rather, advise which to choose. Without knowing the difference, I think I chose UEFI.
2. During booting, I hit DELETE to enter BIOS. But it disregards DELETE. I am not sure if I can suceed, but will try F11, and report back.
Thanks.

it is F11 or F12 .. depending on the machine. If you installed using UEFI then it is best to boot into it. Most CMOSes detect it automatically.

Can you give a brief description of your hardware?

Regards..

---

### Post by ventrical on 2016-06-07
> **palmgrower said:**
> 1. Please explain how UEFI and BIOS are different. Rather, advise which to choose. Without knowing the difference, I think I chose UEFI.
2. During booting, I hit DELETE to enter BIOS. But it disregards DELETE. I am not sure if I can suceed, but will try F11, and report back.
Thanks.

UEFI is Universal Extensible Firmware Interface which , when chosen, runs a software type BIOS from a table provided during the installation process of the OS.  It is supposed to be more secure and faster with unique options (that's the short version) :)

BIOS is that which comes intergrated with your PC (BasicInputOutputSystem) . That is software that is hardwired to the CMOS which is a complimetary software package that comes with most PCs and is the Standard booting method. They are both much more complicated but these are short answers.   

Regards..

---

### Post by oldfred on 2016-06-07
This shows both BIOS & UEFI boot screens. How you boot installer, it then how it installs. But you also have to have actual install booting in same boot mode as you just install. There are three boot modes with UEFI - UEFI with Secure Boot, standard UEFI and BIOS/CSM/Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 
Also best to turn off fast boot in UEFI, or you can have difficulty in getting back into UEFI. This is UEFI setting, not the Windows fast start up settings which also should be off if dual booting with Windows.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi - Efi System Partition [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

UEFI also uses gpt partitioning rather than the 35 year old MBR(msdos) partitioning.

       gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record

[https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

[/URL]

---

### Post by ventrical on 2016-06-07
..and oldfred has the long answer :)

---

### Post by oldfred on 2016-06-07
> ..and oldfred has the long answer :smile:

Many just want a short and sweet answer. :)

---

### Post by ventrical on 2016-06-07
+1

:)

---

### Post by grahammechanical on 2016-06-07
> Should I reinstall 16.04?

Maybe yes. Maybe no. Maybe nothing to do with the OS. A quick web search reveals that Windows users can get this problem. There are a few suggested solutions that work for some but not for others. Here are some links

[http://www.tomshardware.co.uk/answers/id-2305241/fixed-stuck-efi-shell-working-boot-return-bios-msi-read-reply-fix.html](http://www.tomshardware.co.uk/answers/id-2305241/fixed-stuck-efi-shell-working-boot-return-bios-msi-read-reply-fix.html)

[http://www.tomshardware.co.uk/forum/366241-31-startup-problem-stuck-screen](http://www.tomshardware.co.uk/forum/366241-31-startup-problem-stuck-screen)

[http://www.tomshardware.co.uk/answers/id-2577273/stuck-efi-shell.html](http://www.tomshardware.co.uk/answers/id-2577273/stuck-efi-shell.html)

My guess is that the motherboard boot system (UEFI) is detecting a change in the hardware and doesn't know what to do about it. And so it gives you an EFI shell to enter commands that might set things straight. Here are the commands that can be used with a EFI shell prompt.

[https://software.intel.com/en-us/articles/efi-shells-and-scripting](https://software.intel.com/en-us/articles/efi-shells-and-scripting)

Have you added another hard disk or some other kind of hardware?

Regards.

---

### Post by palmgrower on 2016-06-07
Thank you for the advice to select UEFI. (I still don't understand the significance)

During booting F11 > Setup > BIOS screen (same screen if DELETE worked) > Booting sequece: Hard drive first > Save and exit > Restart > same EFI shell screen

Decided to re-install 16.04. During booting F11 > Setup > USB drive first > Save and exit > Restart > Same EFI shell screen.

I cannot do anything with this PC. It is an older MSI FM2 motherboard with AMD A8 or A10 CPU with built-in graphics. No hardware change.

I am going to short CMOS reset, and see if there is a difference. Will write back. Thank you.

UPDATE: Clear CMOS > Restart > DELETE > Line command to setup boot device. Apparently, the hard drive is not a valid boot device. Restart > F11 > USB Key (instead of Setup or Samsung Hard Drive) > Underscore blinks (as if an old terminal waiting for character input) endlessly.

GRAHAMMECHANICAL asked if there was a hardware change. Answer is no. But it rained hard last night. Could this be lightning damage on the motherboard? I am located in Florida, USA's lightning capital.

---

### Post by ventrical on 2016-06-07
> **palmgrower said:**
> Thank you for the advice to select UEFI. (I still don't understand the significance)

During booting F11 > Setup > BIOS screen (same screen if DELETE worked) > Booting sequece: Hard drive first > Save and exit > Restart > same EFI shell screen

Decided to re-install 16.04. During booting F11 > Setup > USB drive first > Save and exit > Restart > Same EFI shell screen.

I cannot do anything with this PC. It is an older MSI FM2 motherboard with AMD A8 or A10 CPU with built-in graphics. No hardware change.

I am going to short CMOS reset, and see if there is a difference. Will write back. Thank you.

UPDATE: Clear CMOS > Restart > DELETE > Line command to setup boot device. Apparently, the hard drive is not a valid boot device. Restart > F11 > USB Key (instead of Setup or Samsung Hard Drive) > Underscore blinks (as if an old terminal waiting for character input) endlessly.

GRAHAMMECHANICAL asked if there was a hardware change. Answer is no. But it rained hard last night. Could this be lightning damage on the motherboard? I am located in Florida, USA's lightning capital.

Try to disable EFI in CMOS and then boot USB stick It should boot from BIOS mode by default.
Regards..

ESD is always a culrpit but I don't think so in this case unless the hdd controlers are not working and you are getting an endless loop. it could also be PSU failing . For what it is worth .. sometimes removing the CPU and resetting it has helped some of my customers in difficult situations with HUD devices  getting static locks on interupt vectors. Check to see if  all your adapter cards are seated flush .. etc..

if none of this works you have endless loop and it is either bricked memory or CPU. Even take out memory sticks one at a time and see.

Regards.

---

### Post by palmgrower on 2016-06-08
It turned out to be hard disk failure. As soon as I replaced the hard drive, the startup USB drive was immediately recognized. Thank you for your help.

---

