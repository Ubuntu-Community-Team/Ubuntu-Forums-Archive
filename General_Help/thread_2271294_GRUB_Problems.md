---
title: "GRUB Problems"
date: 2015-03-29
forum: General Help
---

### Post by chris_s2 on 2015-03-29
So, I am extremely new to Ubuntu and all software associated with it. Due to this, I have made a mistake when installing it. While installing Ubuntu on my External HDD, everything seemed to be going fine. However, the GRUB program was somehow installed on my Internal HDD. Basically, GRUB was installed onto my Internal HDD and not my External HDD. I need to change this, so I can boot Windows without having my external drive connected. Thank you for any help you can provide.

---

### Post by sandyd on 2015-03-29
> **chris_s2 said:**
> So, I am extremely new to Ubuntu and all software associated with it. Due to this, I have made a mistake when installing it. While installing Ubuntu on my External HDD, everything seemed to be going fine. However, the GRUB program was somehow installed on my Internal HDD. Basically, GRUB was installed onto my Internal HDD and not my External HDD. I need to change this, so I can boot Windows without having my external drive connected. Thank you for any help you can provide.

See [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) for a wide array of options to recovering your bootloader.

---

### Post by chris_s2 on 2015-03-29
I have tried every option on that list. None of them seem to work... *sigh* They all end up with me still being stuck at GNU GRUB command line

---

### Post by ajgreeny on 2015-03-29
What version of Windows are you running?

What hardware does the machine have and does it use BIOS or UEFI?

---

### Post by chris_s2 on 2015-03-29
I am running Windows 8, 64 bit. So, with this said, I am running UEFI.

---

### Post by yancek on 2015-03-29
If windows is installed UEFI, then Ubuntu must also be installed in UEFI mode.  Did you do that?  If you can still boot Ubuntu, you should be able to see a FAT32 partition at the beginning of the primary drive which is an EFI partition.  Take a look at it and see if you have both windows/ubuntu efi files.  Another way you could get more detailed information to post here to get help is to run the boot repair script downloaded from the site below.  Just make sure to just select the option to "Create a Boot Info Summary" so you don't make any changes.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chris_s2 on 2015-03-29
Boot Repair link - [http://paste.ubuntu.com/10703860/]("http://paste.ubuntu.com/10703802/")

As for the FAT32 partition, there is one on both drives. The one on the Internal HDD says something about it being mounted at /boot/efi

---

### Post by yancek on 2015-03-29
You have the EFI boot files for both windows and Ubuntu in an EFI partition so that looks right.  You also have syslinux boot code in the master boot record of the first drive (sda) which is not right.  I don't use UEFI so hesitate to make a suggestion.  Maybe someone else more familiar will come along

---

### Post by chris_s2 on 2015-03-29
Oh, okay. So, I have half of the problem solved...sort of. Thank you for showing me the Boot Repair tool to give me the link. Honestly, the problem is more tediously annoying than it is critical.

---

### Post by oldfred on 2015-03-29
You should be able to boot Windows from sda by using the UEFI boot menu and/or the one time boot key often f10 or f12.
But external drives do not normally UEFI boot using the /EFI/ubuntu folder but a /EFI/Boot/bootx64.efi file. We then just copy grubx64.efi into that partition and rename it. Then from UEFI when booting external drive it will use that file. If grub gets major update, you may have to copy again.

You can copy the entire EFI/ubuntu folder from sda, to sdb and update fstab with correct UUID for that efi partition. And then copy just grubx64.efi and rename into a /EFI/Boot folder which you may have to create. Grub will need some of the extra files in /EFI/ubuntu to work correctly.



Not sure with UEFI if it will re-register correctly with UEFI or if you have to manually update entries with efibootmgr.

Can you boot Ubuntu from UEFI menu? 
I thought Toshiba's caused issues.

---

### Post by chris_s2 on 2015-03-29
Alright, I can thoroughly say that I am lost. I have basically no knowledge about this kind of thing. What I do know is very basic in the greater scheme of things.

---

### Post by chris_s2 on 2015-03-29
Yep, I am extremely lost. I have very little knowledge of this type of thing. The knowledge I do have is what caused this problem; not understanding and paying attention to what I am doing.

---

### Post by oldfred on 2015-03-29
Can you boot both Ubuntu & Windows when external drive is plugged in?
Only from UEFI menu, or also from grub menu?

Backup efi partition to another device, first.

It is not a knowledge or how you chose your install. There is a bug or issue with installs to any second drive. 
My own install to sdb an internal drive overwrote my own efi partition on sda. The install on sdb was just a test install and it overwrote the efi of my main working install on sda. But it let me boot into my main install and copy entire efi partition's files to sdb and reinstall the grub on sda.

But external drives are seen a bit differently from UEFI. They boot not from a standard ubuntu folder normally, but from /EFI/Boot/bootx64.efi file.

---

### Post by chris_s2 on 2015-03-30
When the external drive is not plugged in, it brings up the GRUB command line.

---

### Post by oldfred on 2015-03-30
If UEFI, you should be able to go into UEFI boot menu or use one time boot key and choose Windows boot. Does that work? These should be the choices you see:

```
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,0001,0005,2003,2001,2002
Boot0001* [COLOR=#ff0000]Windows Boot Manager[/COLOR]	HD(2,200800,82000,7e530652-c3c4-11e2-a896-f2c4e1b6c204)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-63-A3-58) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa63a358,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-63-A3-58) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa63a358,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0004* ubuntu	HD(2,200800,82000,7e530652-c3c4-11e2-a896-f2c4e1b6c204)File(EFIubuntushimx64.efi)
Boot0005* Ubuntu	HD(2,200800,82000,7e530652-c3c4-11e2-a896-f2c4e1b6c204)File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC
```

---

### Post by chris_s2 on 2015-03-30
I went into the manager and selected setup for my internal HDD, it gave me three options: ubuntu, Windows Boot Manager, and Ubuntu. No idea why it gave Ubuntu twice. Also, my external drive was not plugged in. It allowed me to boot into windows. I still find it a bit tedious to do everytime, but at least I can boot into Windows without having the drive plugged in. Thank you for your help.

---

