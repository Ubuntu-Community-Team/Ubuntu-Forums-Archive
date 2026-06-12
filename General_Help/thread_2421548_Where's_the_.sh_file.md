---
title: "Where's the .sh file?"
date: 2019-06-23
forum: General Help
---

### Post by thumper76 on 2019-06-23
I downloaded a program in a .deb file into Downloads. I clicked on it and I got another screen saying click on install button. I can find nothing. I doc said to run the .sh file, but I can't fine where the .deb put it. I'm new to Ubuntu. The GUI is great, but the command line is a problem.

---

### Post by howefield on 2019-06-23
Thread moved to the "*General Help*" forum.

---

### Post by TheFu on 2019-06-23
> **thumper76 said:**
> I downloaded a program in a .deb file into Downloads. I clicked on it and I got another screen saying click on install button. I can find nothing. I doc said to run the .sh file, but I can't fine where the .deb put it. I'm new to Ubuntu. The GUI is great, but the command line is a problem.

This is non-standard.  Try
```
sudo apt install /path/to/the/dot.deb
```
BTW, expect that installing in this way will break dependencies for the package system in 3-6 months and you will need to remove this specific .deb file in order to patch at that time.

It would be much better to install using a PPA.

---

### Post by gsahli on 2019-06-24
Start over where you "clicked on it." Right-click and "Open with" Gdebi package installer. Click on the Install button there.

---

