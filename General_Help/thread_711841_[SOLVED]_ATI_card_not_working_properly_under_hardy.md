---
title: "[SOLVED] ATI card not working properly under hardy alpha 5"
date: 2008-03-01
forum: General Help
---

### Post by zhouxing on 2008-03-01
I have upgrade from gutsy to hardy alpha 5 but ati x300 card is not working properly. I have installed ati linux driver 8.02 manually but 3d acceleration is not working. fglrxinfo turn out to be mesa instead of ati.

I have tried to use Envy but Envy does not support hardy yet. It can only remove old ati driver, but can not install new one.

I have also tried to install the driver from restricted driver, but it can not log in to  gnome at all. I have to re-install ati linux driver 8.02 to log in to hardy, without 3d capability.

Please any one can help?

---

### Post by PeterJS on 2008-03-01
It's alpha software, head over to the dev forum, let them know it's broken, and consider this a learning experience.

---

### Post by zhouxing on 2008-03-01
I have solved the problem! xorg-driver-fglrx has to be removed by "sudo apt-get remove xorg-driver-fglrx" in the recovery module. Then ati linux driver 8.02 is to be installed manually in recovery module. Then boot into hardy normally, then ati driver works fine.

Attachment is the working ati driver screen shot.

---

