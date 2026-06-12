---
title: "Recovering trash bin"
date: 2007-11-14
forum: General Help
---

### Post by ayampanggang on 2007-11-14
due to my stupidity i deleted trash bin inside the /boot partition

any idea on how to create new trash bin folder?

everytime i want to delete a file there it warns me of not having a trash folder and the file will be permanently deleted.

thank you so much :)

---

### Post by 1/0 on 2007-11-14
Trash bin in /boot???

---

### Post by ayampanggang on 2007-11-14
yeah trash folder within boot. i thought every folder has it's own trash folder?

because all the old data i deleted in the /boot is actually inside a hidden ".Trash-root" folder there (i.e. /boot/.Trash-root). This folder is inaccessible in general, but i become root and mess with it. stupidly rather just deleting the file inside, i delete the whole folder. Now i want it back, lol

thanks for the reply

---

### Post by 1/0 on 2007-11-14
Well... I've never heard of /boot having anything else but the boot files s.a. init, grub, kernel aso. You could create an empty file by:

```

sudo touch /boot/.Trash-root

```

This sounds weired to me but if some package is pointing to that file, give it and you should be fine...

---

