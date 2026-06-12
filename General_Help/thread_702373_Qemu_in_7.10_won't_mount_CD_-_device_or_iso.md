---
title: "Qemu in 7.10 won't mount CD - device or iso"
date: 2008-02-20
forum: General Help
---

### Post by sorceror on 2008-02-20
I built a Windows 98SE QEMU image on a 7.06 machine. I followed the instructions on this page: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) to get kqemu installed and so forth. It works fine on the 7.06 machine, but when I copy the same files over to my 7.10 laptop, no CDROM drive shows up in Windows under QEMU, no matter what value I give for the "-cdrom" parameter. I've tried things like:

qemu -boot c -soundhw sb16,adlib -cdrom cdimage.iso -hda hd.img 
qemu -boot c -soundhw sb16,adlib -cdrom /full/path/to/cdimage.iso -hda hd.img
qemu -boot c -soundhw sb16,adlib -cdrom /dev/cdrom -hda hd.img 
qemu -boot c -soundhw sb16,adlib -cdrom /dev/scd0 -hda hd.img

 Nothing seems to work. Windows shows no CD-ROM drive. One of the reasons I set this up was to play an old game that needs the CD, so it kind of defeats the purpose if I can't use a CD under QEMU. Does anyone have any suggestions or tips? How can I even gather debug info on this?

---

### Post by sorceror on 2008-02-21
Well, I brought up the "Add New Hardware" wizard under Windows, and it showed the IDE controller with the "yellow exclamation point" icon. I mucked with the driver setting, changing it from "Default" to "Both Channels Enabled". After that, a CD drive appeared and things seem to be working fine.

---

