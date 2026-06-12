---
title: "Formated laptop won't boot on Ubuntu 15"
date: 2015-10-26
forum: General Help
---

### Post by wink2 on 2015-10-26
I just formated my laptop to use Ubuntu instead of Win10.
After  a full install via the live CD, the system does not find the new  partition to load. It redirect me to a Sony page who want me to use the  Windows recovery partition (But I deleted it, screw that).

I want to repair it with a live CD, efibootmgr does not seem to have anything related to linux : 

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootNext: 000A
BootCurrent: 0007
Timeout: 0 seconds
BootOrder: 0007,0006
Boot0006* Windows Boot Manager    HD(1,GPT,ef1074c2-fdca-41fd-a3f6-deac09d6da26,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0007* UEFI: KingstonDataTraveler 2.0PMAP    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x4294967217,0x3f,0x7534941)..BO
```

My install loaded grub properly on sda1:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 sda1/
ubuntu@ubuntu:~$ ls sda1/EFI/ubuntu/
grub.cfg        grubx64.efi     MokManager.efi  shimx64.efi  
```

So I add the following boot command : 

```

ubuntu@ubuntu:~$ sudo efibootmgr -c -w -l \\EFI\\ubuntu\\shimx64.efi -L "Ubuntu 15" -p 1 -d /dev/sda

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootNext: 000A
BootCurrent: 0007
Timeout: 0 seconds
BootOrder: 0000,0007,0006
Boot0000* Ubuntu 15    HD(1,GPT,ef1074c2-fdca-41fd-a3f6-deac09d6da26,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* Windows Boot Manager    HD(1,GPT,ef1074c2-fdca-41fd-a3f6-deac09d6da26,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0007* UEFI: KingstonDataTraveler 2.0PMAP    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x4294967217,0x3f,0x7534941)..BO
```

I expect a reboot to start grub, but it doesn't, when I re-test efibootmgr, the command I added is not there anymore.

I tried a boot-repair, no success.
The laptop is a Vaio pro 13. With UEFI but secured boot disabled.


I read about it for 3days, but now need your suggestions.
Thanks

---

### Post by yancek on 2015-10-26
Use the boot repair again and select the option to Create BootInfo Summary and post it here.  Someone should be able to help.

---

### Post by LostFarmer on 2015-10-26
Do you have a password lock on the comps efi firmware/bios setting ?  Not sure if a password could cause your problem or not.  You might be able to enter the data from the comps efi setup page, some comps are friendly and some are not.

Your write command is a little different then when I used efibootmgr to write to firmware, you might try removing the double' \\ '  in the path name. 
\EFI\ubuntu\shimx64.efi

My command :sudo efibootmgr -c -d /dev/sda -p 1 -w -L Pinguy -l '\efi\PinGuy\grubx64.efi'

---

### Post by wink2 on 2015-10-27
Thanks, 

LostFarmer : There is no uefi password, I already tried different params with this command, I tried your, same result :(
Yancek : Here is the Bootinfo :[URL="http://paste.ubuntu.com/12978018/"]http://paste.ubuntu.com/12978018/

[/URL]

---

### Post by LostFarmer on 2015-10-27
It look like your laptop does not like anything but MS Windows. [http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)      [http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi](http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi)

From link 2: [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]      SONY VAIO’s UEFI firmware seems to kick only  “EFI/Microsoft/Boot/bootmgfw.efi” however you put other efi files into  EFI partition(ex: by using BootRepair). Other efi binaries are never  called. You need to replace the binary “EFI/Microsoft/Boot/bootmgfw.efi”  with refind boot manager. 

  Please see also:  [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)[/TD]
[/TR]
[/TABLE]

  You can tell BootRepair to replace EFI/Microsoft/Boot/bootmgfw.efi binary with "grubx64.efi".  (renames grubx64.efi to bootmgfw.efi and replaces said file)

---

### Post by wink2 on 2015-10-27
WHAT THE ... WHAT!

It works, but that does not make any since. I used to loved Sony's hardware, my hearth is broken.
Thank you so much, I've been working days on it. You saved my day.

---

