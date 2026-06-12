---
title: "installation error; carn't installl"
date: 2013-12-08
forum: General Help
---

### Post by abdulsamad342 on 2013-12-08
hey. i'm currently using windows 7; i wanted ubuntu so i downloaded it and started the setup via boot; it goes to first 4 steps and when i choose to keep wind 7 and ubuntu as well it says restart and then the disc comes out pc is restarted and windows 7 opens up.. please help me.. thanks..

---

### Post by fantab on 2013-12-09
Boot with Ubuntu DVD and 'Try Ubuntu without installing', open Terminal [ctrl+alt+T], run the following and post the output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by andrej1741 on 2013-12-09
Do you use (U)EFI BIOS? If you do, turn of secure boot option. Where is GRUB on your machine?

---

