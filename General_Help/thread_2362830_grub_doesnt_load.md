---
title: "grub doesnt load"
date: 2017-06-02
forum: General Help
---

### Post by heron1337 on 2017-06-02
hey i have a problem when im starting computer the grub doesnt load, i have to run bootmenu and select ubuntu from there everytime.plesae help

---

### Post by oldfred on 2017-06-02
What brand/model system?
What video card/chip?

What do you mean by bootmenu?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by heron1337 on 2017-06-02
> **oldfred said:**
> What brand/model system?
What video card/chip?

What do you mean by bootmenu?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

ubuntu 16.04 lts and win10 
amd and intel

i have laptop lenovo g50-80 and i have special key for bootsettings and everytime i want to open ubuntu i need to turn off compute, click the key and choose ubuntu from bootmenu then grub is starting, but when i start my laptop normally with power button its loading win10 immediatly without grub

---

### Post by oldfred on 2017-06-02
That is the UEFI boot menu. You then have Windows 10 as default in UEFI boot order.
But you could have Ubuntu in BIOS mode, and then can only boot they way you are.
If Ubuntu in UEFI boot mode, you may be able to change boot order, either in UEFI or with efibootmgr, but many systems now need a work around.

Post link to summary report to confirm install details.

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170) 

        Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746) 
            T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)

---

