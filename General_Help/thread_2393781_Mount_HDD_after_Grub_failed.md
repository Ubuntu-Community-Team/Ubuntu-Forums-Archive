---
title: "Mount HDD after Grub failed"
date: 2018-06-07
forum: General Help
---

### Post by dynvec on 2018-06-07
I'm basically rewording [Bug #1775657 &#8220;The 'grub-efi-amd64-signed' package failed to inst...&#8221; : Bugs : grub-installer package : Ubuntu]("http://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1775657"), created by me, as I'm nervous about being able to backup what's on the HDD and also if I could manage to get the main OS to boot on that system (including the HDD), I have some unfinished business on it; the latter is not urgent but backing it kind of it. I will basically take the current 1st 5 posts of the bug (#1775657) combining them to make the following (so if you already grasped the former URL, there's no need to read on). **Oh!** All attachments in the OP of the bug with the exception of Screenshot from 2018-06-07 11-42-06.png (error window starting with the bug summary (17.7 KiB, image/png)) are not intentional by me, it's from the bug which was reported; that might be a *good reason to go back to the bug* if one would have started with the, hopefully less convolutely, following.

On an almost 300 Gb HDD, the 1st ~230 Gb was non-*nix and the rest  were old *nixes. I booted on Ubuntu 18.04 LTS non-installing to  partition the drive, deleting the *nixes, stretching the non-*nix  (keeping the beginning to 0). I tried installing[SIZE=1] (18.04 LTS)[/SIZE] which  required me to do steps with the free/unallocated space[SIZE=1] (I was hoping  the installer would use that and make all the steps on it)[/SIZE], so I made  the swap 2 X RAM[SIZE=1] (size)[/SIZE] then made the remaining ~35 Gb ext4 / (root) and  the "Format?" checkbox was present for the only ext4 row/partition. It  failed giving me the error which beginning is the bug link text which  full content is in
[ATTACH=CONFIG]280030[/ATTACH]

 On the same setting, not having rebooted[SIZE=1] (thus booted on Ubuntu 18.04  LTS non-installing on the system which main drive is the almost 300 Gb  HDD)[/SIZE], I tried installing again, using the top-left icon labelled  "Install Ubuntu 18.04 LTS" and kept the previous options up to the 5th,  of 7, option, labelled "Installation type", in which I chose the 1st  option Reinstall Ubuntu 18.04 LTS with description "Documents... will be  kept. Installed software will be kept where possible. System-wide  settings will be cleared." which ended up with the same or quite similar  error; during this there was a warning that partition #5 would be  formatted, and assuming that was the swap, as
[ATTACH=CONFIG]280029[/ATTACH]
show it corresponds, I went ahead. I got the same or similar result both  times; actually this bug is about my 2nd time[SIZE=1] (as my 1st I wasn't  logged in before "sending the problem to developers" or however created  this bug is called)[/SIZE]
The automated choices[SIZE=1] (above the horizontal line which at the bottom has  the choice "Something else")[/SIZE] that didn't involve erasing[SIZE=1] (label starting  with "Erase" and description starting with red "Warning")[/SIZE] was that and  "Install Ubuntu 18.04 LTS alongside Ubuntu 18.04 LTS"
[ATTACH=CONFIG]280028[/ATTACH]
so there was no  automated choice to allow for the non-*nix.

I then restarted the system, and the  previous non-*nix I worked on > 99% time[SIZE=1] (on that system)[/SIZE] would not boot. I could not boot at all. There was some command, I think it was called Grub rescue, which I tried commands to get help in vain.

I'd like to boot on that HDD, but I'm stuck until I can mount it, which I can't seem to do in this environment[SIZE=1] (still in Ubuntu 18.04 LTS non-installing)[/SIZE]. At the very least I need to backup what's on that drive.
Thank you kindly for help.

---

### Post by oldfred on 2018-06-07
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO, be sure to boot Ubuntu installer in BIOS boot mode:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You must have Windows in BIOS boot mode, since drive is MBR(msdos). What version of Windows?
But then you do not want to install Ubuntu in UEFI boot mode, but in same boot mode as Windows or BIOS/CSM/Legacy. How you choose to boot install media is then how it installs.

What brand and model system?
What video card/chip?

While you want BIOS boot mode, this shows both BIOS & UEFI screens.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Only if installing in UEFI boot mode which normally uses gpt partitioning and then you must have an ESP - efi system partition. The version of grub is then grub-efi-amd64. Since not UEFI, nor gpt and you do not have the correct partition for UEFI version of grub to install into, it will not install.

New UEFI hardware has added one more option which you must choose correctly.
UEFI hardware can boot in UEFI mode and for backwards compatibility also in BIOS boot mode. The two modes are not compatible, so best to have all installed systems in same boot mode.
And if you have installed Windows you really need to install Ubuntu in same boot mode.
For both Windows and Ubuntu how you boot install media UEFI or BIOS/CSM/legacy, is then how it installs.
       
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by dynvec on 2018-06-08
> **oldfred said:**
> May be best to see details, you can run from your Ubuntu live installer or any working install
I am running the same as in the OP, I currently don't have any working version of the non-*nix OS I use the--vast--majority of the time. My laptop became non-functioning not long ago and I'm using my desktop.

> **oldfred said:**
> use ppa version not  older Boot-Repair ISO
How can I figure it out? See previous line.

> **oldfred said:**
> be sure to boot Ubuntu installer in BIOS boot  mode
My BIOS has the USB port I'm running this[SIZE=1] (see 1st line)[/SIZE] in higher boot order than any physical drive.

> **oldfred said:**
> Post the link to the Create BootInfo summary report. Is part of Boot-Repair
Is this something I have to run in command line? If it's not part of what I'm running[SIZE=1] (see 1st line)[/SIZE], how do I install? Is it something I can install from the GUI? If so do I use what's in the sidebar, that has a tote icon, labeled Ubuntu Software?

> **oldfred said:**
> You must have Windows in BIOS boot mode, since drive is MBR(msdos).
I'm not sure what you mean but if you look at my 3rd line, if I just don't have any bootable USB stick plugged in when I boot, it does the same as when I could boot from Windows.

> **oldfred said:**
> What version of Windows?
Win 7 64 SP1 (Windows 7 64-bit Service Pack 1)

> **oldfred said:**
> But then you do not want to install Ubuntu in UEFI boot mode, but in  same boot mode as Windows or BIOS/CSM/Legacy. How you choose to boot  install media is then how it installs.
I'm not sure what that means, I'm pretty green in IT.

> **oldfred said:**
>  What brand and model system?
What video card/chip?
FM2-A75MA-E35 ([Overview for FM2-A75MA-E35 | Motherboard - The world leader ... - Msi]("http://www.msi.com/Motherboard/FM2-A75MA-E35.html"))
01G-P3-2615-KR ([EVGA - Product Specs - EVGA GeForce GT 610]("https://www.evga.com/products/specs/gpu.aspx?pn=855c7804-9d98-435a-afea-aabdb0bcda0f"))

I think I should wait for your reply before adressing the rest of your post (#2).

---

### Post by oldfred on 2018-06-08
Did you read the instructions on Boot-Repair link?
It explains how to install it using ppa to any working Ubuntu. And it is a gui based app, although mostly running standard commands in background.

---

### Post by dynvec on 2018-06-08
I'm sorry, I thought the URLs was where to put the report[SIZE=1] (not how to make one)[/SIZE]. Here you go: [http://paste.ubuntu.com/p/TSTFnmtbB2/](http://paste.ubuntu.com/p/TSTFnmtbB2/)

---

### Post by oldfred on 2018-06-08
You have both Windows & Ubuntu installed in BIOS boot mode to MBR partitioned drive.
And two USB flash drives plugged in.
I have found that having flash drive plugged in can change BIOS boot order, but not drive order once mounted by Ubuntu. Best to try booting without flash drives.

Reboot USB flash installer in BIOS mode, Boot-Repair says you booted in UEFI boot mode. So your hardware is newer but your installs are the older BIOS/MBR configuration.

So always be sure to boot in BIOS mode, unless you want to totally erase drive, convert to gpt and  UEFI boot mode.

Grub will not install an UEFI grub to a BIOS/MBR system, normally. And you want the BIOS boot loader anyway.
It looks like you have an old copy of grub in current MBR as it refers to sda8, but install is in sda6. So you have to reinstall grub in BIOS mode to MBR to fix it. use Boot-Repair's advanced mode to totally reinstall grub to MBR of sda.

---

### Post by dynvec on 2018-06-09
> **oldfred said:**
> Reboot USB flash installer in BIOS mode, Boot-Repair says you booted in UEFI boot mode.
How may I do that?

> **oldfred said:**
> So you have to reinstall grub in BIOS  mode to MBR to fix it. use Boot-Repair's advanced mode to totally  reinstall grub to MBR of sda.
I have no idea how to do that. As mentioned in the OP, I used the default installer and found it a bit complicated; so if it's more complicated[SIZE=1] (which I assume it will be)[/SIZE], I will have a bit of a hard time.

---

### Post by oldfred on 2018-06-09
In your UEFI boot menu where you boot flash drive should be two boot entries for flash drive.
One will say UEFI:label and other just label. Where label is name or label of flash drive. The one that is not UEFI:label will boot in BIOS boot mode.
You will have to make sure UEFI Secure Boot is off, but it should already be off if Windows is in BIOS boot mode. And you have to have allow USB boot on in UEFI which also probably is on.
But you may have another setting for UEFI or BIOS/CSM/Legacy boot options. You want the BIOS setting.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

While this is primarily for UEFI booting & installing it has screen shots of both the UEFI boot screen and the BIOS boot screen, so you can confirm which way you have booted.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Then add Boot-Repair like you did and click on its advanced mode. Choose correct tab where it says total reinstall of grub and choose sda as drive to install grub into. Screen shots with details in second link in first post.

---

### Post by dynvec on 2018-06-09
> **oldfred said:**
> In your UEFI boot menu where you boot flash drive should be two boot entries for flash drive.
One will say UEFI:label and other just label. Where label is name or label of flash drive. The one that is not UEFI:label will boot in BIOS boot mode.
I rebooted[SIZE=1] (and my drive still not bootable I had to boot from a USB stick, which was the same as in the OP)[/SIZE] and the following was the text menu, with an asterisk appending the choice. As one may notice, there's no mention of UEFI.

GNU Grub version 2.02

Try Ubuntu without installing 
Install Ubuntu 
OEM install ( for manufacturers) 
Check disc for defects 

Use the &#8593; and &#8595; keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line. ESC to return to previous menu.

---

### Post by oldfred on 2018-06-10
That is the standard UEFI grub menu.

You should also have another boot option in your UEFI menu which is before the grub menu or BIOS boot start screen.

You may need to turn off UEFI boot in your UEFI or turn on Legacy/BIOS/CSM mode. And then select the not UEFI:label boot entry for your flash drive.

---

### Post by dynvec on 2018-06-13
Attached is probably the 2nd recent exploration of the BIOS[SIZE=1] (I probably did more a while back which I don't count)[/SIZE]
[ATTACH=CONFIG]280096[/ATTACH]
; I'm quite glad it offered a screenshot option as I probably would have typed a lot. In my 1st exploration, I could not manage to find how to turn the BIOS mode and I spent some time doing so. I then methodically checked all the options that seemed related in a tree structure, from top to bottom, as deep as I could before going back up.

In the very last screen, where one can save or discard change, at the bottom there was an option Boot Override and luckily I clicked the option that lead me to the old version of Ubuntu; I knew right away that didn't come from any of the USB sticks and I had no media[SIZE=1] (CD, DVD, etc.)[/SIZE] drive so could not be an old media left by mistake. I'm not sure if the right stick which I'm referring to in the OP was in, and if it wasn't I rebooted after plugging it in, but I was glad to find like you mentioned 2 versions of it, with and without the appending "UEFI:", so I chose the option without it then proceeded to do as in the OP again, choosing the 1st automated choice, Reinstall Ubuntu 18.04 LTS, then at the point there was a failure it continued and there was a option added for a bunch of different OS, then after some processes it removed a large portion of them. Once it was finished, I removed the USB sticks then rebooted and finally rebooted in Windows. I was also glad to have a modern version of GNU/Linux as a backup OS on the same drive.

Thank you kindly for all your help [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711").

**Update 1**: 
Well, the uploads here seem to have a low resolution, I made something better at
 [IMG]http://i67.tinypic.com/35isvna.jpg[/IMG] 
but still unreadable. Is there a way I could share it at full resolution?

---

