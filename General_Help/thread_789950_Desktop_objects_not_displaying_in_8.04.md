---
title: "Desktop objects not displaying in 8.04"
date: 2008-05-11
forum: General Help
---

### Post by nathanv117 on 2008-05-11
Installed 8.04. The desktop objects are not showing. Also can not create or add objects to the desktop screen. Nautilus shows the objects under desktop folder. This is valid for both root and user.

Need quick help as I have to make it work by Monday for a training class!
Thanks
Also the same thing is happening when I upgraded from 710 to 804. Here it worked for few hours. I was changing fstab and media entries in both the above environ. Everything else, I tested works, except the desktop problem.

Thanks

---

### Post by dondad on 2008-05-11
> **nathanv117 said:**
> Installed 8.04. The desktop objects are not showing. Also can not create or add objects to the desktop screen. Nautilus shows the objects under desktop folder. This is valid for both root and user.

Need quick help as I have to make it work by Monday for a training class!
Thanks
Also the same thing is happening when I upgraded from 710 to 804. Here it worked for few hours. I was changing fstab and media entries in both the above environ. Everything else, I tested works, except the desktop problem.

Thanks

Try alt-f2 and running gconf-editor. Go to apps then nautilus then preferences. Make sure "show desktop" is checked.

---

### Post by nathanv117 on 2008-05-11
Thanks. I would never have gussed this solutioon.

---

