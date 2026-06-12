---
title: "Ubuntu EFI entry keeps on reappearing in UEFI menu"
date: 2014-12-18
forum: General Help
---

### Post by zebul on 2014-12-18
hi.
I have installed ubuntu 13.10 and later upgraded to 14.04., 14.10

First, I had problem to boot to Ubuntu because I had 2 ubuntu entries in the UEFI firmware menu, when booting.
One is **ubuntu** (without capital letter) pointing to \EFI\ubuntu\shimx64.efi
another one called **Ubuntu** (with a capital letter) pointing to \EFI\ubuntu\grubx64.efi

As I have enable **Secure Boot**, I am only able to boot with the "ubuntu" entry. The "Ubuntu" entries fails and falls back to boot windows even if it is not the next entry in the boot order.
I don't remember, but I wonder if Ubuntu entry is even capable of booting grub/ubuntu if Secure Boot is disabled

That's why, at one point, I decided to remove that "Ubuntu" entry with efibootmgr. And it seems to remove it. But as soon as I reboot it is back there again.

Is it ubuntu (the OS) that re-adds that efi entry, or is it the uefi firmware that does that ? or is it efibootmgr that claims to remove it but does not ?

I have a DELL inspiron 15 (3521)

---

### Post by oldfred on 2014-12-18
I think if the folder exists in the efi partition UEFI will add it back.
What folders do you have in /EFI or if booted in Ubuntu /boot/efi/EFI.

Normal folders are:
       /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

Not seen entries with Capital Ubuntu. So do you have another folder?

---

### Post by zebul on 2014-12-18
I have

```
$ ls /boot/efi/EFI/
Boot/  Dell/  Microsoft/  ubuntu/

```

```
$ efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0003,0004,2001
Boot0000* UEFI Onboard LAN IPv6    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(MAC(74867a652f05,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0001* UEFI Onboard LAN IPv4    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(MAC(74867a652f05,0)RC
Boot0002* ubuntu    HD(1,800,fa000,a701aee6-abe6-4a52-b0b0-937a1c24ad6f)File(\EFI\ubuntu\shimx64.efi)
Boot0003* Windows Boot Manager    HD(1,800,fa000,a701aee6-abe6-4a52-b0b0-937a1c24ad6f)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0004* Ubuntu    HD(1,800,fa000,a701aee6-abe6-4a52-b0b0-937a1c24ad6f)File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* EFI USB Device    RC

```

---

### Post by oldfred on 2014-12-18
Maybe they have changed the grub update to use Capital U. Lots of questions on why there always were two ubuntu entries, and one was always grub and the other shim.

I then think you will keep getting both from grub, not sure why it would automatically reappear immediately, but any grub or kernel update that reruns the grub install commands would register it.

If you are dual booting with Windows, it may also be from the BCD. Windows syncs the UEFI with the BCD and may also sync back?

---

