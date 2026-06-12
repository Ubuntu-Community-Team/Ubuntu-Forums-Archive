---
title: "ubuntu grub menu ??"
date: 2012-12-03
forum: General Help
---

### Post by adym3333 on 2012-12-03
i hv updated ubuntu but now i am not able to see grub menu ... i want that option of grub menu ... am not able to see that menu now .....so what should me done for that i mean for grub menu ..???

---

### Post by oldfred on 2012-12-03
Do you only have one system installed. The default is not to show menu if only Ubuntu installed.

You should be able to get menu by holding shift key from BIOS boot until menu appears.

If you do have other systems then grub2's os-prober many not have found them.

run this to see if it can find other systems.

sudo update-grub

---

