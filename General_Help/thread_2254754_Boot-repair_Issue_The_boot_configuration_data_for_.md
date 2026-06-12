---
title: "Boot-repair Issue: The boot configuration data for your PC is missing or contains err"
date: 2014-11-29
forum: General Help
---

### Post by nemo4 on 2014-11-29
Hey,

I tried dual booting Ubuntu alongside Windows 8 (Lenovo y410p) a few months ago and it worked alright for about a week or so, til it started glitching out.
I tried solving this problem with boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).
The recommended settings didn't help, so I foolishly decided to mess around with the advanced options.
I ticked the option reading "repair file systems" and after this was applied I could no longer boot into Windows.
Whenever I start up the computer it automatically goes to a command line grub. In order to bypass this, I press f12 right when the Lenovo logo shows up. Then I select Windows boot manager from the options listed. This leads me to a blue screen that looks like this: [http://woshub.com/wp-content/uploads/2014/05/win8-repair-efi-bootloader.jpg](http://woshub.com/wp-content/uploads/2014/05/win8-repair-efi-bootloader.jpg)

I've been searching for ages and have attempted countless suggestions from the web but none of them have worked. 
I think the "repair file systems" setting mucked up the Windows boot configuration somehow. If I boot from a boot-repair USB I see a "repair Windows boot files" option under "more options" but unfortunately it is grayed out and unclickable. 

Please help!
Thanks

---

### Post by oldfred on 2014-11-29
Please post link to summary report from Boot-Repair.

Boot-Repair only can do minor repairs to Windows. The Linux ntfs fix tool really just turns on the chkdsk flag, so Windows knows it needs to make repairs. You then need to use f8 to get into repair console. But if booting Windows from grub, it usually is too quick. A few say pressing f8 at the same time as the enter from grub menu works if you try it enough times. 
Best to have Windows repair CD or flash drive to make Windows repairs.
You may be able to use Boot-Repair to temporarily restore a Windows boot loader to MBR and then f8 may work. Then once Windows is fixed and you have made a repair CD or flash drive, restore grub to MBR so you can dual boot.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

