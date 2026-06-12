---
title: "[SOLVED] Installing Skins In Rainlendar"
date: 2008-06-05
forum: General Help
---

### Post by Stoolcat on 2008-06-05
I am trying to install skins in rainlendar, and It says they need to be in the skins folder.  This is located at usr/share/rainlender2/skins   
I am using the öld"version of the skins, so I have to extract there.  But Whenever I try to extract a zip there, it says I don´t have the permission to... 

so, help please..

---

### Post by jpeddicord on 2008-06-05
Ubuntu uses restrictive permissions by default, so you'll need to open the folder as root to copy files there. To do this, press Alt+F2 and in the command box type:

```
gksu nautilus /usr/share/rainlender2/skins
```

Paste the files into that window and they should go in fine. :)

---

### Post by Stoolcat on 2008-06-06
wonderful.  Thanks a bunch.

---

### Post by kindofblue89 on 2009-01-17
You can also try using 
```
sudo mv rainlender_skin_goes_here /usr/share/rainlender2/skins
```

---

