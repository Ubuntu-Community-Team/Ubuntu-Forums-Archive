---
title: "Booting with NTLDR"
date: 2006-11-03
forum: General Help
---

### Post by fm232 on 2006-11-03
I used the method described [here]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")  to dual boot windows xp and followed the instructions exactly but when I try to boot all I get is a blank screen and a flashing cursor. I don't think it has anything to do with the 1024 cylinder limit as lba is turned on in theb bios and I can boot into linux using the super grub cd. Does anyone know why this isn't working?:-k

---

### Post by galego on 2006-11-03
# When I select Linux from the boot menu, I get a frozen "GRUB" (or an "L" in the case of LILO)
# Make sure you created the linux.bin file correctly with the dd command. If you think you ran the command correctly, the problem may be that your /boot partition is beyond cylinder 1024 and your BIOS can't reach it. At system startup, the Windows boot loader lists the choices from boot.ini. When you select Linux, the boot loader then loads the 512-byte linux.bin file, and then BIOS tries to access the /boot partition to run GRUB. Some BIOS implementations can only address the first 1024 cylinders of a hard drive, which corresponds to ~8.5 GB. How do you fix this? Create your /boot partition before cylinder 1024; i.e. before ~8.5 GB.

this is from the troubleshooting note from your how to. give that a shot. :-D

---

### Post by fm232 on 2006-11-04
I am sure that this is not the problem because my bios uses LBA and I can boot into linux via a cd anyway.

---

### Post by fm232 on 2006-11-06
I've still not been able to find a solution. Can anyone help?:-|

---

