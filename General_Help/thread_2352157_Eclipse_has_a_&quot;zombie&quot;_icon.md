---
title: "Eclipse has a &quot;zombie&quot; icon"
date: 2017-02-10
forum: General Help
---

### Post by jonathan90 on 2017-02-10
Hi, I had an old version of Eclipse Mars and I installed Eclipse Neon from their site and deleted the files for Mars, but Eclipse still left a "zombie" icon that's tied to Mars. I deleted the files for Neon, too, but the icon is still there. By the icon I mean when I search "eclipse" in the Search bar, it shows Eclipse as an application, but when I click on it to launch it doesn't do anything and it doesn't show a description. What's going on? Thanks!

---

### Post by howefield on 2017-02-10
Have a look in /usr/share/applications for a stray launcher .desktop file.

---

### Post by jonathan90 on 2017-02-10
I looked in /usr/share/applications and didn't find anything. Also, I installed Eclipse through the Eclipse Installer I downloaded from the Oracle Website instead of a PPA.

---

### Post by howefield on 2017-02-10
Could be in your /home/ folder somewhere, maybe ~/cache, ~/.local or an ~/.eclipse folder...

---

