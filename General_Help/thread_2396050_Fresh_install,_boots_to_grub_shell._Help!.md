---
title: "Fresh install, boots to grub shell. Help!"
date: 2018-07-10
forum: General Help
---

### Post by petersanchez on 2018-07-10
Hey all,

I have a brand new laptop, Lenovo (thinkpad) X1 Carbon 6th gen, fresh install of Ubuntu, installed fine, but upon boot it gives me a grub shell. I have to manually set the prefix, root, insmod linux & normal, then issue 'normal' command to get the grub loader. I've tried boot-repair, grub-update, install-grub, I've wiped the partitions, reinstalled 3x, same thing. Can anyone help?

Here is what I type at grub shell to get the grub loader running and then Ubuntu system up.

grub> set prefix=(hd0,gpt2)/grub
grub> set root=(hd0,gpt2)
grub> insmod linux
grub> insmod normal
grub> normal

This loads the grub boot menu, I select the default (Linux), and Ubuntu boots up normally.

Here is my debug info from boot-repair: [http://paste.ubuntu.com/p/3fHXHYzpQP/](http://paste.ubuntu.com/p/3fHXHYzpQP/)

Note:  this is NOT dual boot situation. Just Ubuntu installed

I'm not really sure what else to try. Any help you can provide is greatly appreciated!

Thanks,

Peter

Edit: Fixed typo in grub shell commands

---

### Post by oldfred on 2018-07-10
It looks like you have done a full drive LVM - logical volume install with encryption & UEFI boot.
Script does not fully parse NVMe drives. Author of bootinfoscript needs someone with an NVMe drive to test changes to that script which is used in Boot-Repair.


It looks you you reformatted ESP - efi system partition several times, /dev/nvme0n1p1.
       Boot0000* Windows Boot Manager    HD(1,GPT,ac42cd42-83dd-11e8-bc6b-8c1645772eb2,0x28,0x640)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...B................
Boot0001* ubuntu    HD(1,GPT,8979f71e-e8f4-4854-9403-75530de7efb8,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0002* grub    HD(1,GPT,9f9afc35-bb0b-4a3c-8193-d4f2b4aaabed,0x800,0x100000)/File(EFIgrubshimx64.efi)

The long number after GPT is the GUID of the ESP. That would only have changed if you reformatted your ESP.

partuuid is GUID.
      
 lsblk -f -o +PARTUUID /dev/nvme0n1
I expect it to show the GUID in your grub entry.
You can see entries as show in script with:
sudo efibootmgr -v
You can delete any entries with old GUIDs.
see 
man efibootmgr
      
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B 

See also this:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)
You really should not have /EFI/grub. 
Not sure if total reinstall of grub from your install or Boot-Repair will fix it, or if you just need to copy /EFI/grub to /EFI/ubuntu. If booted it will be /boot/efi/EFI/grub & /boot/efi/EFI/ubuntu. Post grub.cfg from /EFI/grub folder. Should be three line configfile to boot UUID of latest install. Similar to manual commands you are using.

---

### Post by petersanchez on 2018-07-10
Oldfred - thank you for your reply. 

I removed all entries, wiped the drives again, and reinstalled. Same issue. Here is the output of efibootmgr -v

```

root@thinkpad:/boot# efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0018,0019,001A,001B,001C,001D,001E,001F,0024
Boot0000* grub  HD(1,GPT,ea6b6a8f-edfc-43e9-8571-2f4cd0816e19,0x800,0x100000)/File(\EFI\grub\shimx64.efi)
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu     FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen      FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Regulatory Information        FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0015  Startup Interrupt Menu        FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0016  Rescue and Recovery   FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0017  MEBx Hot Key  FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0018* USB CD        VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0019* USB FDD       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001A* NVMe0 VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001B* ATA HDD0      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001C* USB HDD       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot001D* PCI LAN       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot001E  Other CD      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot001F  Other HDD     VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0020* USBR BOOT CDROM       PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0021* USBR BOOT Floppy      PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0022* ATA HDD       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0023* ATAPI CD      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0024* PCI LAN       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)

```

Here is a small snippet from /boot:

```

root:thinkpad /boot # ls
abi-4.15.0-20-generic     config-4.15.0-23-generic      initrd.img-4.15.0-23-generic  memtest86+_multiboot.bin      System.map-4.15.0-23-generic
abi-4.15.0-23-generic     efi/                          lost+found/                   retpoline-4.15.0-20-generic   vmlinuz-4.15.0-20-generic
acpi_override             grub/                         memtest86+.bin                retpoline-4.15.0-23-generic   vmlinuz-4.15.0-23-generic
config-4.15.0-20-generic  initrd.img-4.15.0-20-generic  memtest86+.elf                System.map-4.15.0-20-generic
root:thinkpad /boot # ls grub/
fonts/  grub.cfg  grubenv  locale/  unicode.pf2  x86_64-efi/
root:thinkpad /boot # ls efi/
EFI/
root:thinkpad /boot # ls efi/EFI/
BOOT/  grub/  ubuntu/
root:thinkpad /boot # ls efi/EFI/BOOT/
BOOTX64.EFI*  fbx64.efi*
root:thinkpad /boot # ls efi/EFI/grub/
BOOTX64.CSV*  grub.cfg*  grubx64.efi*  mmx64.efi*  shimx64.efi*
root:thinkpad /boot # cat efi/EFI/grub/grub.cfg
search.fs_uuid 5021822d-4528-44ad-905d-008338404291 root
set prefix=($root)'/grub'
configfile $prefix/grub.cfg
root:thinkpad /boot # cat efi/EFI/grub/BOOTX64.CSV
shimx64.efi,ubuntu,,This is the boot entry for ubuntu
root:thinkpad /boot # ls efi/EFI/ubuntu/
fw/  fwupx64.efi*
root:thinkpad /boot # ls efi/EFI/ubuntu/fw
root:thinkpad /boot #

```

---

### Post by petersanchez on 2018-07-10
Here is my /boot/grub/grub.cfg:

[https://paste.ubuntu.com/p/ZDPRp4SJtp/](https://paste.ubuntu.com/p/ZDPRp4SJtp/)

---

### Post by jeremy31 on 2018-07-10
Reinstall without internet connection and see if it boots.  There has been some issues recently with updating during install

---

### Post by oldfred on 2018-07-10
Your grub.cfg in /boot/efi/EFI/grub is correct.
I would first try copying it to /boot/efi/EFI/ubuntu.

But others have found just reinstalling grub works.
One of the users posted this bug, please add to it, as they almost immediately ignore single bugs, at least with2 someone will look at it. It really needs 5 reports or more to become a priority.
       Ubuntu 18.04 similar error /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042) 
    
If booted into your install.
       [https://ubuntuforums.org/showthread.php?t=2396045](https://ubuntuforums.org/showthread.php?t=2396045)
$ sudo apt-get install grub-efi-amd64
$ sudo update-grub 
    
Why are you at root? Ubuntu uses sudo for Admin purposes.
       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by petersanchez on 2018-07-10
> **oldfred said:**
> Your grub.cfg in /boot/efi/EFI/grub is correct.
I would first try copying it to /boot/efi/EFI/ubuntu.

This worked. It now boots straight into grub! Thank you!
    
> **oldfred said:**
> If booted into your install.
       [https://ubuntuforums.org/showthread.php?t=2396045](https://ubuntuforums.org/showthread.php?t=2396045)
$ sudo apt-get install grub-efi-amd64
$ sudo update-grub 

I'd already done this previously with no luck.
    
> **oldfred said:**
> Why are you at root? Ubuntu uses sudo for Admin purposes.
       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)

Only because the permissions in /boot/efi were strict and I was avoiding typing sudo so much for the purposes of the paste. I use sudo for all root operations normally.

Thank you again for your help!

---

