---
title: "Can't use Windows theme-Permission Denied"
date: 2017-09-10
forum: General Help
---

### Post by 1jarwolf on 2017-09-10
I inserted a scrot screenshot of the error I am getting. it says the Windows 10 theme is used however, it will not actually use it as the permission is denied. How can I change the permissions so that the theme configuration will be able to use it correctly?

---

### Post by deadflowr on 2017-09-10
```
sudo chmod -R 755 /usr/share/themes/Windows\ 10\ Dark
```
the permission currently is 700 giving only the owner (root) access.
Lightdm is not root so it would not have any access to the files.
755 will make it accessible for everyone

---

