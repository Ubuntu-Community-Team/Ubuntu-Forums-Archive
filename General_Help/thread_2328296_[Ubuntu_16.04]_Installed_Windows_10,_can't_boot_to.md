---
title: "[Ubuntu 16.04] Installed Windows 10, can't boot to it."
date: 2016-06-19
forum: General Help
---

### Post by dr-cono on 2016-06-19
Hi, i have ubuntu 16.04 installed and i wanted to install Windows 10. I installed it and it skiped the grub and went straight to Windows 10, i grabbed a copy of boot-repair usb disk and tried to run recommended settings but i got this error:
[COLOR=#000000][FONT=monospace]GPT detected. Please create a BIOS-Boot partition (>1MB, unformattedfilesystem, bios_grub flag). This can be performed via tools such as Gparted.Then try again.[/FONT][/COLOR]

After an hour of so of trying things i finally managed to boot into ubuntu running this:
[COLOR=#111111][FONT=Consolas]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

[/FONT][/COLOR]but now i can't boot to windows, can't run boot-repair in recommended settings, in advanced settings tried settings sda1 (where the UEFI partition is) but grub2 isn't detecting my windows. Also, i have one entry of an old windows that's incorrect.
Here's my bootinfo summary generated from boot-repair:
[http://paste2.org/n9MB2emg](http://paste2.org/n9MB2emg)
[COLOR=#000000][FONT=monospace][/FONT][/COLOR]

---

### Post by dr-cono on 2016-06-19
Here's my efibootmgr -v if it helps somehow:
> BootCurrent: 0000Timeout: 2 seconds
BootOrder: 0000,0002,0001,2001,2002,2003
Boot0000* Windows Boot Manager  HD(1,GPT,fae7a125-e7c6-4570-9978-536f1ab52ece,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3................
Boot0001* Ubuntu        PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(1,GPT,fae7a125-e7c6-4570-9978-536f1ab52ece,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)A01 ..
Boot0002* Windows Boot Manager  HD(1,GPT,fae7a125-e7c6-4570-9978-536f1ab52ece,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0003* Unknown Device:       HD(1,GPT,fae7a125-e7c6-4570-9978-536f1ab52ece,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0004* Unknown Device:       HD(1,GPT,fae7a125-e7c6-4570-9978-536f1ab52ece,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0005* TOSHIBA MQ01ABD100                    BBS(PCMCIA,TOSHIBA MQ01ABD100              ,0x500)................-.f.......f.A.f...................................|.........A.........................
Boot0006* Unknown Device:       HD(2,GPT,5fca3638-90aa-4118-8d5a-09ed4f4191fa,0x12c800,0x96000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0007* Unknown Device:       HD(2,GPT,5fca3638-90aa-4118-8d5a-09ed4f4191fa,0x12c800,0x96000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0008* Unknown Device:       HD(2,GPT,5fca3638-90aa-4118-8d5a-09ed4f4191fa,0x12c800,0x96000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot000A* Unknown Device:       HD(2,GPT,5fca3638-90aa-4118-8d5a-09ed4f4191fa,0x12c800,0x96000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot2001* EFI USB Device        RC
Boot2002* EFI DVD/CDROM RC
Boot2003* EFI Network   RC




---

### Post by oldfred on 2016-06-20
That Boot-Repair is asking for a bios_grub partition, then it is trying to reinstall grub in BIOS boot mode. You have Windows in UEFI boot mode, so want to keep Ubuntu in UEFI boot mode.

Can you boot the Ubuntu entry?
You show many duplicate unknown description entries that  are shim. You probably should delete those.
What brand/model system?

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

