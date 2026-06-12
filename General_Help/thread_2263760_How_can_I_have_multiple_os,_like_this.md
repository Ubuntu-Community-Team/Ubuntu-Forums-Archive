---
title: "How can I have multiple os, like this?"
date: 2015-02-03
forum: General Help
---

### Post by Higgins909 on 2015-02-03
What I've done so far is:
shrink one of my drives in windows 7 didn't add a drive letter or something so it remains a empty partition to use.

got the latest ubuntu desktop 64bit, installed it to a usb and booted and installed with manual partitions, this is where I kinda got lost..
I have 3 drives my ssd that has windows 7 on it then this small storage drive that I want to install a bunch of os on the mess around on then a big storage drive, thats just a storage drive.

the first time I tried to install it failed...  I tried to install the grub with the windows 7 grub thing, tried it again, but moved the grub to the small storage drive, right on the drive, not the partition I was making ext4 (not sure it if would have even let my put it on the ext4 if I tried) works pretty well, few problems...

but in order to boot to it I have to spam/hold F11 and then select the drive and then it goes though the grub thing.
How Could I have made it so when the computer turns on I have a 10ish second choice to choose what os to boot and have a changeable default os?
have win7 and want to install ubuntu, lxle, and zorin to work with windows 7.

right now I'm more horsing around with these os's, but in the end, probably ubuntu will end up along side windows, on my ssd.

Thanks,
Higgins909

---

### Post by CantankRus on 2015-02-03
When you install Linux, choose to install grub to that drive not the partition.
eg say windows is on /dev/sda and you install Linux to /dev/sdb  .....install grub to **/dev/sdb**  not the partition **/dev/sdb[COLOR="#FF0000"]1[/COLOR]**.

Then you need to select the Linux disk as the boot drive in the Bios.
This will keep your windows boot intact.
Should you remove ubuntu you need only revert to the windows disk as the boot drive in the bios.

---

### Post by yancek on 2015-02-03
> shrink one of my drives in windows 7 didn't add a drive letter or something so it remains a empty partition to use.

That would not matter as Linux uses different naming conventions for hard drives and partitions.  Also, windows is incapable of recognizing a Linux filesystem much less writing or even reading it.  Take a look at the second post at the link below for a basic overview

[http://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme](http://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme)

And installing the bootloader as suggested in the post above.

---

### Post by oldfred on 2015-02-03
As soon as you have multiple drives and/or multiple installs, you should learn to use bootinfoscript and/or Boot-Repairs summary report.

I run a new update of bootinfoscript with every rsync backup, so I have documented my current configuration. The bootinfoscript is the first part of Boot-Repairs Summary Report which includes some extra info that can be useful for debugging boot issues.

       Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[URL="http://sourceforge.net/projects/bootinfoscript/files/latest/download"]http://sourceforge.net/projects/bootinfoscript/files/latest/download

      [/URL]
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    [URL="http://sourceforge.net/projects/bootinfoscript/files/latest/download"]
[/URL]

---

### Post by Higgins909 on 2015-02-03
> **CantankRus said:**
> When you install Linux, choose to install grub to that drive not the partition.
eg say windows is on /dev/sda and you install Linux to /dev/sdb  .....install grub to **/dev/sdb**  not the partition **/dev/sdb[COLOR=#FF0000]1[/COLOR]**.

Then you need to select the Linux disk as the boot drive in the Bios.
This will keep your windows boot intact.
Should you remove ubuntu you need only revert to the windows disk as the boot drive in the bios.

It seems I failed to notice that windows 7 was in grub... probably because it gets put on my portrait monitor in landscape mode...
But what will happen when I try to install 2 more os on that same drive? do I need to put the grub on the same drive? or will it conflict with the ubuntu grub?

and when I install it onto my ssd, would I then put the grup on my ssd, next/on to windows 7 boot loader?

---

### Post by oldfred on 2015-02-03
With BIOS/MBR partitioning, you only have one MBR per hard drive. So last install owns MBR and controls booting. If Windows is installed last then it only boots Windows. That is why you need bootinfoscript to know which system has control of MBR. You can manage that when you install only if using Something Else to install.

If you have a new UEFI system then every install is a folder in the efi partition. Somewhat like having multiple MBRs one one drive. But versions of Ubuntu if not renamed may overwrite each other, so efi partition backups may be important.

---

### Post by CantankRus on 2015-02-03
> **Higgins909 said:**
> It seems I failed to notice that windows 7 was in grub... probably because it gets put on my portrait monitor in landscape mode...
But what will happen when I try to install 2 more os on that same drive? do I need to put the grub on the same drive? or will it conflict with the ubuntu grub?


I have a dedicated drive for just Linux installs.
First install is an ubuntu lts release (which I plan to keep the longest) and I install grub to the drive ...eg /dev/sdb.
Then I install the next alpha/beta version and lastly have a partition for testing other distros.
When installing the next alpha/beta version and other distros I choose the partition of my install (eg /dev/sdb5) to install grub so as not to overwrite my original grub.

This means after installing any extra distro I need to log into my Ubuntu lts install and run 
**sudo update-grub** to add the new install to grub and appear in the boot menu.

> and when I install it onto my ssd, would I then put the grup on my ssd, next/on to windows 7 boot loader?
You don't have to, but is the least confusing option. Install to drive not partition.
Just remember if you remove Ubuntu on your ssd you will need to repair the windows7 mbr.

---

### Post by kevdog on 2015-02-04
> **oldfred said:**
> As soon as you have multiple drives and/or multiple installs, you should learn to use bootinfoscript and/or Boot-Repairs summary report.

I run a new update of bootinfoscript with every rsync backup, so I have documented my current configuration. The bootinfoscript is the first part of Boot-Repairs Summary Report which includes some extra info that can be useful for debugging boot issues.

       Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[URL="http://sourceforge.net/projects/bootinfoscript/files/latest/download"]http://sourceforge.net/projects/bootinfoscript/files/latest/download

      [/URL]
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    [URL="http://sourceforge.net/projects/bootinfoscript/files/latest/download"]
[/URL]

Too bad such a tool couldn't be available for MacPlatforms!!!

---

