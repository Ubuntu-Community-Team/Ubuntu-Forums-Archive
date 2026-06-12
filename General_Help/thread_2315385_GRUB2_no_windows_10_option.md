---
title: "GRUB2 no windows 10 option"
date: 2016-02-28
forum: General Help
---

### Post by jimangel2001 on 2016-02-28
So, I recently installed ubuntu 15.10 in my HDD alongside with Windows.
 Everything was OK until I installed Kali Linux too. When I booted I couldnt find a Windows option.
 I said "OK" just go into Ubuntu, reinstall GRUB run boot-repair and this should fix everything, but no it didn't work.
Any ideas?

Thanks in advance.

---

### Post by oldfred on 2016-02-28
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And probably best to boot into Ubuntu and reinstall its grub. Are all systems UEFI or all systems BIOS boot?

---

### Post by jimangel2001 on 2016-02-28
Here is the report [http://paste.ubuntu.com/15230657/](http://paste.ubuntu.com/15230657/)

And, I am a still a noob, I don't know anything about UEFI/BIOS boot.

---

### Post by grahammechanical on 2016-02-28
This will explain why we need to have all OS installed either in EFI mode or BIOS/Legacy/CSM mode.

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[/URL]If you are loaded into Ubuntu please run this command and watch the printout to screen.

```
sudo update-grub
```

Does the printout  include a listing for a Windows boot loader? If it does run this command

```
sudo grub-install /dev/sda
```

Regards

---

### Post by jimangel2001 on 2016-02-28
```
Generating grub configuration file ...Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Kali GNU/Linux Rolling (kali-rolling) on /dev/sda7
done

```
That's what I get.

I think that I should mention the fact that I used a Windows 7 disc to repair the bootloader from there but even this didn't recognize the Windows 10 partition. (therefore I didn't do anything)

---

### Post by oldfred on 2016-02-28
It looks like you have an UEFI system, but all operating systems are installed in BIOS boot mode.
And you have grub in MBR.

But this is issue:
>  Windows not detected by os-prober on sda2.



And that is most often caused by Windows being either hibernated or needing chkdsk. And new Windows 8 or later uses always on hibernation or fast start up. Linux will not normally mount hibernated Windows and grub cannot boot hibernated Windows. 

You have to turn off the Windows hibernation.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

You can use your Windows repair flash drive or install flash drive in its repair console to restore a Windows boot loader. FixMBR command.
Best to keep Windows repair flash drive as Boot-Repair can only do minor repairs to Windows.
You may be able to use Boot-Repair to restore a Windows type boot loader to MBR as that is one of the few repairs it can do. 

After fast start up is off, use Boot-Repair to restore grub2's boot loader to MBR. 
And run this to add Windows to grub menu.
sudo update-grub
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by jimangel2001 on 2016-02-29
I did what you said and here is my boot screen [http://i.imgur.com/U9WUNG1.jpg](http://i.imgur.com/U9WUNG1.jpg)
sda2 [http://i.imgur.com/3nRKaXp.jpg](http://i.imgur.com/3nRKaXp.jpg)
sda1 [http://i.imgur.com/ZVkM2sI.jpg](http://i.imgur.com/ZVkM2sI.jpg)

---

### Post by oldfred on 2016-02-29
Original copy of script showed the boot flag on sda1, but no boot files.
And you have bootmgr but not /Boot/BCD in sda2.

Did you boot Windows repair flash drive and run a full set of repairs? You either need /Boot/BCD in sda2 and boot flag moved to sda1 or all boot files in sda1 where boot flag is currently. Only Windows can make those repairs. If just BCD missing some third party tools may repair/create new BCD.

Depending on version of grub, it has not been updated to say "Windows 10". It often goes thru list of valid entries and if no version found defaults to recovery mode. Best not to normally boot into recovery mode as that can create partition table issues. But if you look at details of grub's chain load entry and see that is is really booting main Windows Boot partition then you can boot the entry that says recovery mode.

---

