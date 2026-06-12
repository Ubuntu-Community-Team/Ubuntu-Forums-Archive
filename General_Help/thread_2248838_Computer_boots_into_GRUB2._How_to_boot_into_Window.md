---
title: "Computer boots into GRUB2. How to boot into Windows directly?"
date: 2014-10-17
forum: General Help
---

### Post by dana5 on 2014-10-17
Hi everyone, 

When I turn on my computer, grub2 starts automatically. It doesn't give me an option, I just turn on my computer and GRUB2 immediately pops on my screen. I tried booting Windows using a variety of commands (trying to set root and then booting that, but I kept getting errors and more and more frustrated). Anyway, seems that if I write exit, then Windows will load. How do I make it that Windows is the only thing my computer has and boots into?

MORE DETAILS: 
Here is the screen I see when I start up my computer: 
[ATTACH=CONFIG]257298[/ATTACH]

[FONT=arial][COLOR=#333333] These are the steps I took to end up in the above pickle:[/COLOR]
[/FONT]
[LIST]
[*][FONT=arial]Opened disk manager. Deleted the partitions I believed to be Ubuntu (99% sure I allocated 100GB right next to my D: partition, and that's what I deleted and merged with D). There were 3 partitions next to D, which I believe somehow all belonged to Ubuntu, and when added together were 100GB. They were all marked as "Healthy primary partition"[/FONT]
[*][FONT=arial]Went into the UEFI settings and enabled Secure Boot, disabled CSM[/FONT]
[*][FONT=arial]Restarted and landed on the above screen.[/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]If I call [FONT=courier new]ls [/FONT]I get the following options:[/COLOR]
[FONT=courier new](hd0) (hd0,gpt6) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)[/FONT]
[COLOR=#333333]When I do[FONT=courier new] ls (hd0,gpt1)[/FONT] I get[/COLOR]
[FONT=courier new]Filesystem is fat[/FONT]
[COLOR=#333333]Everything else returns[/COLOR]
[FONT=courier new]Filesystem is unknown[/FONT]

[/FONT]

---

### Post by oldfred on 2014-10-17
Is Windows installed in UEFI or BIOS boot mode.

If UEFI , you should be able to go directly into UEFI menu and choose to make Windows first boot option. You have to manually delete ubuntu entry in efi folder and in UEFI menu entries.

IF BIOS you have to install a Windows or Windows compatible boot loader to the MBR, best to always do that before deleting Ubuntu as the rest of grub in in Ubuntu so system will not boot with grub still in MBR.

Best to use your Windows repair CD or flash drive. But you can use an Ubuntu live installer to directly load the lilo boot loader which works like the Windows boot loader in the MBR, or use Boot-Repair to install a Windows type boot loader.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

      Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 [http://www.sevenforums.com/](http://www.sevenforums.com/)
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by dana5 on 2014-10-31
Awesome, that worked! For others that run into the same problem, this is what worked for me: 

[COLOR=#333333][FONT=UbuntuRegular]First of all, to exit GRUB2, I ran exit twice and my computer boot would finally boot into Windows.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I then had to go to my UEFI settings:[/FONT][/COLOR]

[LIST]
[*]Open charms bar (swipe from the right in)
[*]Click Settings
[*]Change PC settings (located at the bottom)
[*]Update and Recovery
[*]Recovery
[*]Under Advanced Start Up, click Restart now
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Once there, I was able to open the Boot menu from under the advanced options and I deleted the ubuntu entries.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Afterwards, I reinstalled Windows, though I don't think that's necessary. If you want to reinstall, that option is also under the PC Settings -> Update and Recovery -> Recovery.[/FONT][/COLOR]

---

