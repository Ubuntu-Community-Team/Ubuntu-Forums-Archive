---
title: "notebook won't boot after power shutdown."
date: 2013-11-24
forum: General Help
---

### Post by ogward on 2013-11-24
Hey there!
Yesterday I was listening to music on Youtube without the adapter connected, when I saw that the power level was getting critical i went to get the adapter and when i came back the notebook was already shut. Now when I try to boot it there is only a blinking cursor.

Any suggestions?

Best regards

---

### Post by germanix on 2013-11-24
I had a similar problem yesterday. Fixed it by starting the laptop in "save mode", on my machine this means holding down the F2 button whilst booting. On your machine this could be a different button. Once in save mode you have the opportunity to fix things. I choose the option "fix broken packages" and the "update.grub" option, thereafter I then rebooted and all was fine. Hope this helps.

---

### Post by ogward on 2013-11-24
when I select "update grub bootloader" I get the error.
*/usr/sbin/grub-probe: error while loading shared libraries: libudev.se.0: cannot open shared object file: no such file or directory*
I get the same error when i selct "check all file systems".

---

