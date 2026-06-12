---
title: "BIOS Update -&gt; no more dual Boot Grub screen -&gt; farewell ubuntu?"
date: 2018-02-26
forum: General Help
---

### Post by Riemens on 2018-02-26
After using both windows and ubuntu for quite some time as a dual-boot setup (grub), I'm unable to access my ubuntu now. I was running in (W10) some hardware problems and I thought updating my BIOS would do the trick.

All went well until I discovered I couldn't access Ubuntu anymore.

I tried Win10 Safe Mode restart, a bunch of Commands 'ebcedit something something ..', troubleshooting startup, accessing the BIOS or UEFI screen (1 of the 2), but ubuntu isn't shown in there.

In the past - from what I can remember - is in the Windows boot screen I could go to Ubuntu, but now that isn't visible.

What to do?

I'm using an Acer laptop btw, Ubuntu is running for a long time now on a separate partition.

It was hard enough for me to get this running, doing this all over isn't really an option.

Regards,

- I

---

### Post by cruzer001 on 2018-02-26
Could it be the "trust" setting?

[https://ubuntuforums.org/showthread.php?t=2384706&p=13738847#post13738847](https://ubuntuforums.org/showthread.php?t=2384706&p=13738847#post13738847)

And there is Boot-Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sloughin on 2018-02-26
I am struggling with this same issue.  Running an ASUS VivoMini VC66 with a UEFI BIOS.  Windows 10 update murdered Grub.  After much difficulty I have managed to get the BIOS to disable secure boot. I can use the Compatibility settings on Legacy to boot from the Boot-Repair ISO image on a DVD, but when I click "Repair" it complains that the BIOS is in Legacy mode not EFI mode.  It seems Boot-Repair wants UEFI, but UEFI refuses to load Boot-Repair (even when I set the DVD as boot option #1) and boots right into Windows 10.  I am very unhappy with UEFI -- it seems to have been designed to keep people from using non-Microsoft operating systems, or at least that's how it was implemented on this computer.

---

### Post by Riemens on 2018-02-27
Ok I got it fixed - :) - everything is fine now.

What I did:
1. I' m not 100% sure, but I think I restarted windows by holding SHIFT key and clicking the restart button in windows 10.
2. This opened a menu, that I have visited many times before. You'll find troubleshooting options here and some more. When I clicked thru a couple of menus I found an option which said. 1. Windows 10 - 2. HDsomethingsomething (a code of numbers and letters, I didn't recognize it).
3. I selected the second option and the original GRUB screen loaded for the first time, like it always used to do.
4. I selected Ubuntu to run and like cruzer001 said I installed and ran the Boot-Repair program
5. When Boot-Repair was ready, this is what I got: " [COLOR=#000000][FONT=Calibri]If your computer reboots directly into Windows, try to change the boot order in your BIOS.[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]For example you can boot into Windows, then type the following command in an admin command prompt:[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi" 
6. I went to windows and used the bcdedit command.

7. I' m not entirely sure where stuff went right, but I still didn't got the GRUB screen when I rebooted. So the following steps I'm not sure what I did in what sequence.
8. I went to the UEFI / BIOS (F2 on startup) and changed the boot order from 1. Windows 2. HDetc.. (same one as in step 2) to 1. HDetc (step 2) 2. Windows.
9. I also changed at one point in Windows 10 the option for 'what the power button does' and unchecked the 'fast start-up' box.

I was actually experiencing very slow boot times in Windows 10 (50 to 100% slower) so I undid step 9 and it maybe is the same as it used to be because of the last step.

In BIOS / UEFI I also had settings where I could change between UEFI or LEGACY, but I still had it unchanged at UEFI. Also for Secure Boot, I kept it on active.

The only thing that changed for me now is that my GRUB screen has more options now. Options used to be 1. Ubuntu 2. Windows 10 3. 'Some third option' . Now there are about 2 or 3 more. UEFI boot manager, boot UEFI etc.. But I'm happy with the way it is now :).

I hope this helps.
- I[/FONT][/COLOR]

---

