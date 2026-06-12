---
title: "Grub configuration to boot Windows from USB-harddisk?"
date: 2007-04-03
forum: General Help
---

### Post by DaOane on 2007-04-03
Hi!

I have Ubuntu 6.10 installed onto the internal harddisk of my laptop. I have an external USB-harddisk with two ntfs-partions whereof the first hosts the Windows XP operating system and the second is just for data. The usb-harddisk is recognised as a harddisk in the bios and boots correctly when I specifiy it. Unfortunately it always looses its priority after I booted Linux (without the device attached) which makes it necessary to edit the bios-settings when I want to boot Windows after a Linux session.

Therefore I want to make grub to boot Windows - so far without success.

1. How does grub recognise a usb-harddisk? In the BIOS it is recognised as harddisk and not as external storage, under Linux, of course, as a scsi-device, but in grub?

2. Are there any peculiarities with the chainloader when adressing a bootloader on an usb-device?

... maybe somebody has done this before and has a solution ready?

Thanks for any help.
Cheers,

Henning

---

### Post by Herman on 2007-04-03
It should be recognised as just another hard disk (if your BIOS supports booting with the USB disk). Here are a few links that might be of some help,I hope.

You could try to find it with [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

You could read about how to install grub to the USBdisk, [How to add Grub to your USB thumb drive]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.") Although that's not about your exact problem, there still might be something there that could help, especially this link, [SUCCESS - Breezy loaded on external USB drive !]("http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub") 			([IMG]http://ubuntuforums.org/images/uf/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub") [2]("http://ubuntuforums.org/showthread.php?t=80811&page=2&highlight=Success+breezy+booted+from+USB+grub") [3]("http://ubuntuforums.org/showthread.php?t=80811&page=3&highlight=Success+breezy+booted+from+USB+grub") ... [Last Page]("http://ubuntuforums.org/showthread.php?t=80811&page=49&highlight=Success+breezy+booted+from+USB+grub")) DaBruGo

I hope you'll fins something there useful, I'll be back later and I'll have more time then.

Regards, Herman :)

---

### Post by DaOane on 2007-04-05
Thanks Herman!

Your pages are very helpful and straightforward.
I had a go on the command line interface again and tried to boot Windows there. As I have it on a ntfs-partition, the grub tools are not of much use. However, I could verify my external harddisk as hd1 and the Windows partition as (hd1,0). So far, so good - it's easy now, I thought, standard proceedure:

rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

and the result:

"A disk read error occurred. Press Ctrl+Alt+Del to restart"

When I leave out the map commands it results in a "Starting up ...", but nothing happens.

When I use the commands as written above, but use chainloader /ntldr I get the following error: "Error 17: cannot mount selected disk". This is peculiar. As long as I had Windows on the same harddisk as Ubuntu, grub had no problems to recognise the ntfs file-system. Is there a way to tell grub to use ntfs? Any other ideas? Thanks.

Cheers,

Henning

Henning

---

### Post by Herman on 2007-04-05
Hello again DaOane,
Grub does not attempt to recognize any NTFS filesystem.

Other ideas?
Yes, I have an idea, you said "As long as I had Windows on the same harddisk as Ubuntu, grub had no problems to recognise the ntfs file-system". What if you[ install Grub in the usbdisk?]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.")
You'll need a small partition somewhere on the disk, (it can be at the end of the disk, it should work anywhere), and install Grub. Grub installs with it's stage1 files in part of the MBR, and stage1_5 in the next fifteen sectors. That won't touch your Windows filesystem because that doesn't begin until sector number 63, if you want to check, do 'sudo fdisk -lu', and you'll see. Grub's stage2 files are the main part of grub, and those normally live in a filesystem, but you don't need to install an operating system. Grub is practically a tiny operating system on its own. 
So you just to make a new partition of say 50 to 100 MiB and make a new folder in it named /boot. Then to copy any grub directory to it and install your usbdisk's grub to the usbdisk's MBR.
After that you may need to edit the menu.lst in the installed hard disk to boot the MBR of the usbdisk, or, until you get around to that, [boot with your F8 or F12 key]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key"). You may also need to edit the usbdisk's grub's menu.lst file again too.

Regards, Herman :)

---

### Post by DaOane on 2007-04-05
Thanks Herman for the tips. Do I understand you right: You mean to have grub on both harddisks, i.e. chainloading grub-on-usb-disk from grub-on-internal-disk which then chainloads ntldr-on-usb-disk? This might be a solution, I'll give it a try.

Henning

---

### Post by Herman on 2007-04-05
Yes, that's the idea, it sounds like you understand me alright. 
You can make a backup of the IPL for the Windows bootloader in the usbdisk's MBR too if you like, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd") (just in case you might want to restore things back to the way they were).

Regards, Herman :)

---

