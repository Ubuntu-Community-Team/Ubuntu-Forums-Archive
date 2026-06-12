---
title: "Can no longer boot into OS after Windows 11 update"
date: 2023-11-04
forum: General Help
---

### Post by browndonahue on 2023-11-04
I'm running a Windows 11 dual boot with Kubuntu 22.04(LTS) on a lenovo laptop. I opened Windows 11 after almost 3 months and the system did a  complete update of it's firmware which stopped showing me the grub menu  during boot and the system now directly boots into Windows, I tried to  do the recommended boot-repair using live USB but it gave some errors. 

Here's the link of the boot repair report: [https://paste.ubuntu.com/p/JbJRGDMZSx/](https://paste.ubuntu.com/p/JbJRGDMZSx/)

It looks like my previous windows install might have been removed but I would like a second opinion.

---

### Post by MAFoElffen on 2023-11-04
It said it was fine and would not recommend any repairs...

and this:
```

BIOS/UEFI firmware: N2JET99W (1.77 )(1.77) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0020
Timeout: 0 seconds
BootOrder: 0000,0002,001A,001B,001C,001D,001E,001F,0020,0021,0022,0023,0011
Boot0000* ubuntu    HD(1,GPT,9bc2c69a-0a3d-408d-8edd-2f7528ba64ae,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* Windows Boot Manager    HD(1,GPT,91b1ddd2-2895-425b-b62c-77e584dd0866,0x800,0x219800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...F................

```
Shows everything as fine... The UEFI boot order shows Ubuntu, then Windows.

If you shut it down cold. Then boot it, what does it do?

EDIT: Where is Windows again???

---

### Post by tea for one on 2023-11-05
> **browndonahue said:**
> the system now directly boots into Windows
> **browndonahue said:**
> It looks like my previous windows install might have been removed but I would like a second opinion.
I'm a bit confused by your description of the situation.
How can your PC boot into Windows 11 if it was removed?
[COLOR="#0000FF"]Line 40[/COLOR] - 0 OS detected
Boot-repair was unable to find any OS, surprising if Windows 11 boots OK.

Anyway, first of all, I would have a look at the UEFI settings and disable anything connected to security.
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)
Enable Microsoft 3rd Party UEFI CA

---

### Post by MAFoElffen on 2023-11-05
I stand corrected from my earlier post. I have no idea what is going on, from what you said an described.
```

nvme0n1                                                                                                                       
&#9500;&#9472;nvme0n1p1               vfat        6DFE-0B64                              91b1ddd2-2895-425b-b62c-77e584dd0866             
&#9500;&#9472;nvme0n1p2               ext4        d4bb9687-8e49-4a25-bd4a-8fe41d6f20b3   2beacb5d-836b-41f9-b1d7-7db4a8b9e2b4             
&#9492;&#9472;nvme0n1p3               LVM2_member zpyNyi-7cbS-XWpE-BscY-P3Vs-Mp25-XmeYac af1f42d3-9607-43be-9469-433f995e3ba6             
  &#9492;&#9472;ubuntu--vg-ubuntu--lv                                                                                                     

```
^^^ Wait??? (I looked closer.) How can it "after a Windows 11 update, goes directly to Windows 11..." Where  is Windows in that? Is there a disk missing there?

Because if Windows was there, and if that was the only disk, there would be a gap in the disk, where 3 more partition were... (2 Microsoft Reserved and at least 1 NTFS) And there is not.

Even though Windows shows in the UEFI, I do not see another OS there beside Ubuntu...

---

