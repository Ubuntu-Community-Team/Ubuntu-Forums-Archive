---
title: "Dual boot: Grub Menu no longer showing"
date: 2015-10-12
forum: General Help
---

### Post by owen11 on 2015-10-12
Approximately a month ago my laptop stopped showing the Grub menu on startup. I had used this guide [http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580) to setup my dual boot.


    bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi


Has not fixed the issue like it did when I updated to windows 10 a while ago.


I have run boot repair using a live usb of ubuntu.
[http://paste.ubuntu.com/12684245/](http://paste.ubuntu.com/12684245/)


Any help with how to resolve this issue would be greatly appreciated!

---

### Post by oldfred on 2015-10-12
Your grub.cfg/menu only shows Ubuntu. When you only have one system in grub it assumes you want to boot just that so it does not show menu by default. With UEFI you have to press escape key for grub menu to appear.

But does this add Windows to grub menu so then you will have it all the time?
sudo update-grub

You show 5 Windows boot entries in UEFI? You really should only have one.
      ```
 BootOrder: 0001,000A,0007,0009,0008,0006,0000
Boot0000* Windows Boot Manager	HD(2,96800,32000,a0bbce14-8342-4a47-b3cf-49f30cd6192e)File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu	HD(2,96800,32000,a0bbce14-8342-4a47-b3cf-49f30cd6192e)File(EFIubuntushimx64.efi)
Boot0006* Windows Boot Manager	HD(2,96800,32000,a0bbce14-8342-4a47-b3cf-49f30cd6192e)File(EFIMicrosoftBootbootmgfw.efi)
Boot0007* Windows Boot Manager	HD(4,108800,ed73800,97f195db-e2c1-47eb-9d5b-b62bba09724b)File(EFIBootbootx64.efi)
Boot0008* Windows Boot Manager	HD(4,108800,4f22cdc,97f195db-e2c1-47eb-9d5b-b62bba09724b)File(EFIBootbootx64.efi)
Boot0009* Windows Boot Manager	HD(4,108800,5003cdc,97f195db-e2c1-47eb-9d5b-b62bba09724b)File(EFIBootbootx64.efi)
Boot000A* UEFI: SanDisk Cruzer Blade 1.27	ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,20,1dd17e0,00000000)..BO


```

There are two versions, not sure which is correct.
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
    
If you delete the wrong one you can add a new one:
 if ESP sda2, you have to specify drive & partition
sudo efibootmgr -c -d /dev/sda -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by owen11 on 2015-10-12
I dont think that i made it clear that it always boots to windows. My only way of accessing ubuntu at all is via instillation media. 
When I try to run "[COLOR=#000000]sudo update-grub" it gives me /usr/sbin/grub-probe: error: failed to get canonical path of '/cow'
[/COLOR]

---

### Post by oldfred on 2015-10-12
You have to run the grub update from inside your install. Or chroot into it, or use Boot-Repair.

But if only booting Windows, does not BCD give the ubuntu option if you added that to BCD? I think that is then a reboot into Ubuntu then.

Can you use one time boot key, often f10 or f12, check manual to choose Ubuntu.

What brand/model system. Some only boot Windows and need work arounds. The BCD entry is only one of many.

Other work arounds, most copy /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi and boot a UEFI hard drive entry in UEFI. You may have to add that entry to UEFI.

Details in link in my signature and these:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

