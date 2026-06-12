---
title: "After BIOS reset to default settings grub is gone...."
date: 2013-03-03
forum: General Help
---

### Post by sushi80 on 2013-03-03
Hi all

i have (had) a dual boot ubuntu-Win8 on UEFI and i also have Mageia on another partition. Everything was working fine, Grub was able to run Ubuntu - Win 8 and Mageia without problem but after a  BIOS reset to default settings Grub seems gone and on startup i only have Mageia boot loader (this load fine) but _Ubuntu is gone and Win8 doesn't load.

I've used a LiveUSB of secureUBuntu and run boot repair few times with no luck

my bios now is set with Boot mode as LEgacy Support and Boot priority as Legacy First

Changing to  Boot mode as LEgacy Support and Boot priority as UEFI first doesn't help

here last boot repair

[http://paste.ubuntu.com/5582077/](http://paste.ubuntu.com/5582077/)

Help Please!!!

---

### Post by zero2xiii on 2013-03-03
Hay

This is simply a drive sequence issue. Usualy F11/12 during boot will bring up a "boot device selection screen". Try selecting a different drive untill your grub prompt pops up.
Then set your first boot device to this drive.

 Good luck :)

---

### Post by sushi80 on 2013-03-03
Unfortunately is not that easy....i can only choose between "ubuntu" "Ata HDD" "CD" and "Network"

if i select "ubuntu" i get the grub from Mageia
if i select "ATA HDD"  i get again the grub from Mageia

it seems that the EFI menu from ubuntu is gone....

---

### Post by zero2xiii on 2013-03-03
Hay,Well grub's menu seems fine from the pastebin post.What are your grub options? Can you get to a grub terminal and manually mount and boot the OS?Refer to the following links for details on how to accomplish this tedious task:
 [http://forums.justlinux.com/showthread.php?152790-How-to-use-Grub2-to-boot-Linux-manually](http://forums.justlinux.com/showthread.php?152790-How-to-use-Grub2-to-boot-Linux-manually)
[http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/](http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/)
[http://www.novell.com/communities/node/12424/loading-linux-kernel-manually-using-grub-sles](http://www.novell.com/communities/node/12424/loading-linux-kernel-manually-using-grub-sles)
[URL="http://forums.justlinux.com/showthread.php?152790-How-to-use-Grub2-to-boot-Linux-manuallyhttp://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/http://www.novell.com/communities/node/12424/loading-linux-kernel-manually-using-grub-slesPossibly"]
[/URL]Possibly try chainloading your grub from Mageia, the above links cover that as well in some form.
Good luck

---

### Post by sushi80 on 2013-03-03
it seems like the EFI partition is skipped at boot.... for my understanding the Ubuntu grub should be there....

the grub loaded from mageia has 3 options 

boot mageia  --- works
boot mageia (safe mode)  ---works
boot windows  ----- broken

---

### Post by zero2xiii on 2013-03-03
Yes,

So that is a problem. But try and boot ubuntu from the grub you get at the moment. There might be a whole different reason (such as time out) which causes that grub not to come up, but you must first try and make sure that ubuntu is still bootable.

:?

---

### Post by oldfred on 2013-03-03
You have grub legacy (Mageia?) in MBR. So if you are booting that, you are booting in BIOS mode not UEFI mode. You still show ubuntu & Windows in efi partition so if you boot in UEFI mode you should see those. But BIOS mode installs are not compatible with UEFI mode installs so you cannot easily dual boot Mageia and Ubuntu. UEFI and BIOS write system info somewhat differently, so you have to go back into UEFI/BIOS and turn on or off to boot in system installed in that mode. Since Mageia seems to be using grub legacy, it may have even have a efi boot capability and only a few Linux will boot with secure boot systems.
So turn off legacy/BIOS boot, turn on UEFI boot but do not turn on secure boot. Some system do not make it clear on UEFI settings, so you have to figure out how yours works.

         Under Windows 8 Secure Boot, all PCs, no matter what operating system they actually run, must include several Microsoft-owned keys. 
 The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

---

### Post by sushi80 on 2013-03-03
I was able to recover my system using gparted, i run a check of EFI partition and at the end i finally got again ubuntu Grub

the only problem is that during many test i've done i've also re-installed ubuntu :D 

anyway now grub can load Ubuntu - Win8 and Megeia (using 30_os-prober)

---

### Post by zero2xiii on 2013-03-03
Glad to hear :)

Please mark thread as solved then...

---

