---
title: "boot-repair stuck on os-prober"
date: 2012-10-18
forum: General Help
---

### Post by Us1ingaeph on 2012-10-18
Hey,

So i decided to try out 12.10 last night and it ended up messing up 'grub_efi_64' aswell as other things  >:(  I tried to run boot-repair on a live cd but it's continously looking for operating systems (>45 minutes). Ive tried manually mounting the EFI partition and then all my partitions and it still wont start up. Ive also tried manually fixing the grub following these intructions: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

however the folders were slightly different in my partition so "/mnt/EFISYS/efi/grub/" became "/mnt/EFISYS/EFI/ubuntu/"

also there was only 1 file in the folder called something like grub_x_efi_64 whereas after following the tutorial there are now lots.

Any help appriciated.

---

### Post by Us1ingaeph on 2012-10-18
fixed via this tut: [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)

---

