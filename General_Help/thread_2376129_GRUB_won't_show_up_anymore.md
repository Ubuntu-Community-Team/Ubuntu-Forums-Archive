---
title: "GRUB won't show up anymore"
date: 2017-10-30
forum: General Help
---

### Post by mattiav31 on 2017-10-30
I have Ubuntu 16.04LTS installed in dual boot with Windows 8.1 

Since this morning I cannot access to Ubuntu since GRUB won't show up.

I tried to reinstall the GRUB from the live CD using the tool boot-repair, but nothing has changed: here [https://paste.ubuntu.com/25852552/](https://paste.ubuntu.com/25852552/) the result of the analysis. 

From the live CD I also used the tool efibootmgr and run the command: sudo efibootmgr -v and this is the result:

[INDENT]   BootCurrent: 0002  
      Timeout: 0 seconds  
      BootOrder: 0001,0000,0002,2001,2002,2003  
      Boot0000*   ubuntu    HD(3,GPT,9d3e440a-ea3a-49e3-b3cb-946e22675a11,0x363800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
      Boot0001* Windows Boot Manager    HD(3,GPT,9d3e440a-ea3a-49e3-b3cb-946e22675a11,0x363800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
      Boot0002* Ubuntu  HD(3,GPT,9d3e440a-ea3a-49e3-b3cb-946e22675a11,0x363800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC
      Boot2001* EFI USB Device RC  
      Boot2002* EFI DVD/CDROM   RC  
      Boot2003* EFI Network RC
 [/INDENT]
Can anyone please help?

---

