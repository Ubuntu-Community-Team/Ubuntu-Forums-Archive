---
title: "[SOLVED] panel missing"
date: 2008-03-11
forum: General Help
---

### Post by Samrat Rao on 2008-03-11
i have ubuntu 7.10 installed on my desktop and so i have administrative rights. for the first time i added a user today, but when i login with my username and password, i find that both the panels are missing and hence i am not able to do any work. the user that i have added has the panels at his disposal. fortunately i have the kde environment installed as well and i have the panels correctly working in this environment. deleting the new user has no effect on the gnome environment ie i do not get back the panels. pl help as i like the gnome version better.:(

---

### Post by Oldsoldier2003 on 2008-03-11
> **Samrat Rao said:**
> i have ubuntu 7.10 installed on my desktop and so i have administrative rights. for the first time i added a user today, but when i login with my username and password, i find that both the panels are missing and hence i am not able to do any work. the user that i have added has the panels at his disposal. fortunately i have the kde environment installed as well and i have the panels correctly working in this environment. deleting the new user has no effect on the gnome environment ie i do not get back the panels. pl help as i like the gnome version better.:(

log into a gnome session and ALT+F2 then type gnome-panel

that should launch your panels. or you could right click the desktop and make a launcher for gnome panel.

after doing this save your session and logout. when you log back in the panels should load.


If you find yourself having to do this often you can delete the .gnome folder in your home directory. it will reset your gui and the problem should  clear itself up.

---

