---
title: "grub-editenv: error"
date: 2014-02-14
forum: General Help
---

### Post by Sinead_Mannion on 2014-02-14
grub-editenv: error: cannot open the file /boot/grub/grubenv.new./etc/default/speech-dispatcher


Hello,

I'm new to Ubuntu, I'm using 12.04. I got the above error. I had my computer on when the electricity was shut off for a few minutes, would this have affected it?
please help me, I cannot get into my Ubuntu 

thanks

sinead

---

### Post by jeanjd63 on 2014-02-14
Hello

You can try to boot on a LiveCD/USB and do on partition / a :
**sudo  fsck -f -y  /dev/sdXY**      you have to replace XY by good values
and then you reboot.

---

