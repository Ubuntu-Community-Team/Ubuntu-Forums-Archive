---
title: "BIOS will not recognize Ubuntu after BIOS reset. Why?"
date: 2017-11-20
forum: General Help
---

### Post by ultratamale on 2017-11-20
[ATTACH=CONFIG]277611[/ATTACH][ATTACH=CONFIG]277612[/ATTACH]

In one picture you can see that Ubuntu is shown as a boot option. In the other picture you can see that Ubuntu is not shown, this was after the BIOS was reset. In both images the hard drive is shown.

1) Why does Ubuntu show separately from my hard drive? That is the only hard drive and the USB stick is not plugged in here.
2) Why doesn't the option to boot Ubuntu appear after a BIOS reset? And selecting the hard drive does not allow me to boot Ubuntu.
3) My BIOS reset during a remounting of my CPU, which meant taking my whole PC apart. Can this happen on its own? I didn't recall reseting my BIOs, but it is possible I move the BIOS reset pin doodad.

---

### Post by oldfred on 2017-11-20
BIOS reset or upgrade of BIOS, normally changes everything back to defaults or as purchased and before any changes.
In my BIOS I had so many settings, I had to take photos, so I knew what I had changed whenever I updated BIOS.

Newer UEFI systems save many settings and allow screen shots which can be saved.

If UEFI system, you can run efibootmgr to readd Ubuntu entry. 
If BIOS you are just booting hard drive.

---

### Post by ultratamale on 2017-11-20
When you say "If UEFI system, you can run efibootmgr to readd Ubuntu entry" what do you mean? Run it where?

---

### Post by oldfred on 2017-11-20
See links in my signature & See also 
man efibootmgr

It defaults to ESP - efi system partition being on sda1.
First check current entries, you must be booted in UEFI mode on live installer or any working install. In terminal:
sudo efibootmgr -v

This then adds a new Ubuntu entry:
 sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition  


 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

