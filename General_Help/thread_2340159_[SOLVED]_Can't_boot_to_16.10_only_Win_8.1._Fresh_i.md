---
title: "[SOLVED] Can't boot to 16.10 only Win 8.1. Fresh install"
date: 2016-10-16
forum: General Help
---

### Post by sebastian1978 on 2016-10-16
Freshly installed 16.10. Can't boot to Grub. Only Win 8.1. Only option is load to Ubuntu in menu Recovery from Windows . 

Also after I load 16.10 system clock changes to 3 hours in bios and Windows.

---

### Post by oldfred on 2016-10-16
What brand/model system?
Can you choose Ubuntu from UEFI boot menu?
Did you install Ubuntu in UEFI boo tmode and Windwos is in UEFI boot mode?
       
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 [URL="http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows"]http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows
[/URL]
 Clock and some boot settings like fsck, login,   tmp retain time.
/etc/default/rcS
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no  

[URL="http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows"]
[/URL] 

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by sebastian1978 on 2016-10-16
Thanks!

I have Sony VAIO notebook SVF15A1S9R
I already sent pastbin today. I tried Boot Repair from Ubuntu it gave me error:
[http://paste2.org/A4B1JZs8](http://paste2.org/A4B1JZs8)

Also I solved the problem. I opened EasyUEFI Free for Windows and disabled the item Windows Boot Manager because changing the boot order didn't worked.
For solving time problem I run in terminal
sudo hwclock --localtime --adjust

---

### Post by oldfred on 2016-10-16
Sony has not been dual boot friendly.

Most have to copy shimx64.efi to bootx64.efi and add an UEFI boot entry to boot hard drive, not ubuntu entry.
Boot-Repair probably did the copy, but does not add the boot entry into UEFI.
And the bootx64.efi may have been your Windows boot entry?

---

