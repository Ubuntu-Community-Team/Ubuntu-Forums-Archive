---
title: "Going straight to windows - grub2 not working"
date: 2015-12-28
forum: General Help
---

### Post by joao10 on 2015-12-28
Hello
I tried so many things from different places including boot repair and nothing seems to be working. I can only boot into windows. 
Last thing I tried was from this site [http://deshack.net/ubuntu-dual-boot-grub-doesnt-start/](http://deshack.net/ubuntu-dual-boot-grub-doesnt-start/)
and the output of [COLOR=#333333][FONT=Roboto Condensed]efibootmgr -v is:

[/FONT][/COLOR][COLOR=#333333][FONT=Roboto Condensed]> BootCurrent: 0010
Timeout: 1 seconds
BootOrder: 2003,2001,2002
Boot0000* Grub2Win EFI    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\grub2win\grub2win.boot.efi)WINDOWS………x…B.C.D.O.B.J.E.C.T.=.{.4.a.2.f.b.1.8.4.-.0.e.3.e.-.1.1.e.4.-.a.5.9.e.-.b.d.a.0.f.2.7.6.a.c.d.4.}…5…………….
Boot0001* ubuntu    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* kali    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\kali\grubx64.efi)
Boot0003* Windows Boot Manager    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS………x…B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}…5…………….
Boot0004* UEFI: Network Card PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54bef7832b80,0)/IPv4(0.0.0.0:00.0.0.0:0,0,0)..BO
Boot0008* Windows Boot Manager    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS………x…B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}…5…………….
Boot0009* UEFI: Network Card PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54bef7832b80,0)/IPv4(0.0.0.0:00.0.0.0:0,0,0)..BO
Boot000A* UEFI: Network Card PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54bef7832b80,0)/IPv6([::]:[::]:,0,0)..BO
Boot000B* UEFI: Network Card PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54bef7832b80,0)/IPv6([::]:[::]:,0,0)..BO
Boot000C* UEFI: TOSHIBA MQ01ABD100    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/HD(7,GPT,d86c58dc-28f3-43b8-9194-a6f28779580a,0x6f222000,0x32000)..BO
Boot000E* kali    HD(2,GPT,b4f4942a-0b9d-11e3-a0ba-a69b9f1ac104,0x200800,0x32000)/File(\EFI\kali\grubx64.efi)
Boot000F* UEFI: TOSHIBA MQ01ABD100    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/HD(16,GPT,ad549dce-ecf5-4277-924f-1724e3bfcd1d,0x6f306000,0x32000)..BO
Boot0010* UEFI: USB DISK 2.0 PMAP PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(2,0)/HD(1,MBR,0x0,0x80,0x7a8780)..BO
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

I hope you can help me out as I'm really desperated because I have to work on ubuntu. Thanks![/FONT][/COLOR]

---

### Post by oldfred on 2015-12-28
You show this as your boot order.
 BootOrder: 2003,2001,2002
None of those are your installs, just other devices. I would normally make a network boot last as you probably do not use it and it has to check network and try that first making boot slower.
      
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 2,1

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

Many Toshiba now also have been modified like HP & Sony to only boot by description. And only valid description is "Windows". So we have to add a work around to boot the default/fallback entry of /EFI/Boot/bootx64.efi and make that entry really grub.

              [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
    
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

Same instructions in link in my signature. 


[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

