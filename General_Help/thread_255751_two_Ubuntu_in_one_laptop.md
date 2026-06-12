---
title: "two Ubuntu in one laptop"
date: 2006-09-11
forum: General Help
---

### Post by MaaSTaaR on 2006-09-11
Hello ...

i am using now Ubuntu 6.06 in my laptop (in hda6 partition) , and i want to install it in hda1 partition , that's mean i will have two Ubuntu in my laptop .

my question can i get all programmes and device drivers (modem) which installed in the old Ubuntu , and put them in the new Ubuntu ? :)

My English is worst ](*,)

---

### Post by mssever on 2006-09-12
You should be able to use ```
cp -a
``` to copy files across. In fact, you could copy everything across, and as long as you altered Grub as appropriate, it should work just fine. I question, however, what you would accomplish by moving Ubuntu to hda1. Performance-wise, there shouldn't be any difference between the two, and you could use hda1 for anything you want without re-installing (e.g., /home, file storage, etc.).

---

