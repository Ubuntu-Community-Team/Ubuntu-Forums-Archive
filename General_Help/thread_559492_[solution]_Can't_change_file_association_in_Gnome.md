---
title: "[solution] Can't change file association in Gnome"
date: 2007-09-25
forum: General Help
---

### Post by NoWhereMan on 2007-09-25
You might know already that to **change app-file associations** you just left click on your file and pick from the **open with tab** one app of the list.

Hower sometimes this** does not work**.

The reason for me was that ~/.local/share was **owned by root**. I renamed the directory and let nautilus re-create it! 

now it should work again (w00t!)

Hope this helps

---

