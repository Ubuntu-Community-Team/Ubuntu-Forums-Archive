---
title: "Installing Wine with &quot;Add/Remove Applications&quot;"
date: 2008-05-04
forum: General Help
---

### Post by Neumy on 2008-05-04
I'm having no luck installing Wine with "Add/Remove Applications". Half way through I get an error:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-Oubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-Oubuntu4_i386.deb)
404 Not Found 

My guess is that all I need to do is change the server "ca.archive.ubuntu.com" to one that works, but I can't seem to find any configs for the Add/Remove application.

Has anyone encountered this before? Any advice where I'm going wrong? 

Thanks!

---

### Post by vishzilla on 2008-05-04
To change the server go to System>Admin>Software Sources. In the drop down menu under download from choose 'other' and click on 'choose best server' and select the server that is chosen. Close and reload.

---

### Post by NightwishFan on 2008-05-04
You can change servers under: System -> Administration -> Software sources. That should fix the issue, although it seems impermanent. If the issue remains file a bug report on Launchpad.net.

---

### Post by zvacet on 2008-05-04
I don´t know which Ubuntu version do you use,but [this]("http://www.winehq.org/site/download-deb") is another way to install wine.

---

### Post by Neumy on 2008-05-04
Thanks for your help. As soon as I choose another server, Wine installed perfectly.

---

### Post by NightwishFan on 2008-05-04
I am glad it works for you. :KS

---

