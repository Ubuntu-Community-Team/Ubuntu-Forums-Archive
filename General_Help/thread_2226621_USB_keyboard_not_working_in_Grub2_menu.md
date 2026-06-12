---
title: "USB keyboard not working in Grub2 menu"
date: 2014-05-28
forum: General Help
---

### Post by akimbo337 on 2014-05-28
Hi everyone!

I've got a really strange problem with my current system, a win7-kubuntu14.04 dual-boot: When booting via Grub2, I cannot use my usb keyboard in the boot selection menu.

Things I tried:
[LIST=1]
[*]Checked the (UEFI) bios for USB related settings and made sure USB keyboards are available at boot time. BTW both OS are installed in non-UEFI mode. 
[*]Added 'GRUB_PRELOAD_MODULES="usb usb_keyboard ehci ohci uhci"' to /etc/default/grub, ran 'grub-mkconfig -o /boot/grub/grub.cfg' and subsequently 'update-grub2'. My USB keyboard now worked fine in the Grub menu, but when I selected any entry, I returned the error "grub error: disk (hd0,msdos5) not found". A simple "ls" in the grub rescue console resulted in the same error. 
[*]Started via LiveCD and restored a backup of grub.cfg — after that it's the USB keyboard not working again, but the system boots the default menu choice. 
[*]Installed grub-efi-amd64 (replacing grub-pc) and ran mkconfig and update-grub2 again, but it resulted in the same error (disk (hd0,msdos5) not found). Again replaced grub-efi-amd64 with grub-pc. 
[/LIST]

I have got no remaining clue how to approach this error and would really appreciate any constructive input from you!

Please find below some additional infos about my setup:

_**[SIZE=2]Disk layout[/SIZE]**_
```
# LANG=en_US.UTF-8 fdisk -l /dev/sda

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063c9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   419430399   209611776    7  HPFS/NTFS/exFAT
/dev/sda3       419432446   500117503    40342529    5  Extended
/dev/sda5       419432448   498020351    39293952   83  Linux
/dev/sda6       498022400   500117503     1047552   82  Linux swap / Solaris
```

_**Installed Grub packages**_
```
# LANG=en_US.UTF-8 aptitude search grub|grep -E ^i
i   grub-common                     - GRand Unified Bootloader (common files)   
id  grub-efi-amd64-bin              - GRand Unified Bootloader, version 2 (EFI-A
i A grub-gfxpayload-lists           - GRUB gfxpayload blacklist                 
i   grub-pc                         - GRand Unified Bootloader, version 2 (PC/BI
i   grub-pc-bin                     - GRand Unified Bootloader, version 2 (PC/BI
i   grub2-common                    - GRand Unified Bootloader (common files for
i   kde-config-grub2                - Configuration module for the GRUB2 bootloa
```

_**Configuration files (via Dropbox)**_
[grub.cfg]("https://www.dropbox.com/s/lebocqbfwcrrxq1/grub.cfg") — boots default entry but does not let me use my keyboard.
[grub.cfg.mod]("https://www.dropbox.com/s/w6qxc494rnbd119/grub.cfg.mod") — lets me use my keyboard, but doesn't boot entries.

_**Misc. Infos**_
Mainboard Asus P9D WS; firmware version 1804 (latest)
Boringly normal Cherry USB keyboard
Windows 7 64-Bit non-UEFI install
Kubuntu 14.04 64-Bit non-UEFI install
any info missing here, let me know ...

Again, I would be really happy if anyone could let me know how to fix this issue.

Best regards.
Marcel

---

### Post by oldfred on 2014-05-30
Some have posted that Gigabyte boards may need IMMOU setting for USB3 ports to work.

Are you using USB2 port?
Different model had this setting?
 Asus m4a87td  core unlocker feature on usb3 was causing the problem


 Enabling USB Legacy Support - If keyboard does not work.
[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

---

### Post by Francis_Kearney on 2015-01-02
I have the same problem with different hardware. I also have the windows 7 and Ubuntu dual-boot. I used to have the Grub configuration working fine with Ubuntu 13.10, but on upgrade to 14.04 Grub started failing with the hd0,msdos5 error that you report above.

When I remove the:

GRUB_PRELOAD_MODULES="usb usb_keyboard ehci ohci uhci"
GRUB_TERMINAL_INPUT="usb_keyboard"

lines from the /etc/default/grub and update-grub, the keyboard won't work but the Grub menu doesn't fail with the error.

It seems something about loading those keyboard drivers is causing the problem, even though the keyboard works when they are loaded!
I'm very interested in if you solved this and how. Here's my default grub file, but it's not too interesting except for those lines above:

[http://pastebin.com/TRQ6f8hb](http://pastebin.com/TRQ6f8hb)

---

### Post by Francis_Kearney on 2015-01-04
Ok, I got a fix.

I guessed (as you did) that the new vesrion of Grub with Ubuntu 14.04 was somehow buggy around preloading the keyboard modules. I tried several things to get them to load properly, with no luck.

But I know that the Grub bundled with 13.10 worked fine, so I rolled back to that. Here's how I did it:


[LIST]
[*]Added Saucy (Ubuntu 13.10) apt repository
[LIST]
[*]sudo add-apt-repository "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main"
[*]More help on this step: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[/LIST]

[*]Purged 2.02 Beta Grub
[LIST]
[*]sudo apt-get purge grub-common
[/LIST]

[*]Found 2.00 version of grub from saucy repository
[LIST]
[*]sudo apt-get update
[*]apt-cache policy grub-pc  #See the new 2.00-19ubuntu2 version available
[/LIST]

[*]Install the 2.00 version of grub
[LIST]
[*]sudo apt-get install grub-pc=2.00-19ubuntu2
[*]This didn't work right away, had to manually install:
[/LIST]
[/LIST]
[INDENT=3]grub-pc-bin=2.00-19ubuntu2
[/INDENT]
[INDENT=3]grub-common=2.00-19ubuntu2
[/INDENT]
[INDENT=3]grub2-common=2.00-19ubuntu2
[/INDENT]
[INDENT=3]with this same command. There's probably a way to do that automatically that I don't know. 
[/INDENT]

[LIST]
[*]Reinstall grub in the MBR
[LIST]
[*]sudo grub-install /dev/sda  #Or whatever drive/partition you use to boot
[/LIST]

[*]Add the properties back to /etc/default/grub, GRUB_PRELOAD_MODULES="usb usb_keyboard ehci ohci uhci" and GRUB_TERMINAL_INPUT="usb_keyboard"
[*]sudo grub-update
[*]Reboot and use your keyboard at the grub menu!
[/LIST]

After this, Ubuntu's software update wants me to upgrade to the 2.02 beta grub packages again. So you have to deny that update or goodbye keyboard at the grub menu.
I think you can stop Ubuntu's update from trying to update those grub packages by marking them 'hold' in the package manager:

echo "grub-pc hold" | sudo dpkg --set-selections

I did this for all the grub packages (got them with "dpkg --get-selections | grep "grub").
 
I'm not sure that Grub/Ubuntu knows about this bug, but I'm not sure where to file. If anyone knows point them this way.

---

### Post by oldfred on 2015-01-05
bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

Grub bugs are here, you should search on keyboard issues and see if similar one has been posted. There seem to be several keyboard issues posted.
You do have to create another login to launchpad.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bugs?orderby=-id&start=0](https://bugs.launchpad.net/ubuntu/+source/grub2/+bugs?orderby=-id&start=0)

---

