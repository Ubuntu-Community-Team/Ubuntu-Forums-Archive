---
title: "Icon/Theme Manager problem."
date: 2005-03-20
forum: General Help
---

### Post by malegria on 2005-03-20
After having put the EdgeIcons in the ~/.icons folder, my Theme Manager ended up looking like this:

[IMG]http://www.geocities.com/lavie_est_ailleurs/Screenshot.png[/IMG] 

Also the EdgeIcons don't work. I've tried with other icon sets and it's the same thing. I've tried removing the icon sets and it still looks the same. Could this just be a bug?
I previously installed the Suade icon-set with no problems.

Any ideas?

---

### Post by Xian on 2005-03-20
Reapply the Human theme, close the theme manager and then re-open.
Does it draw the theme options correctly?

If not try renaming the ~/.icons folder then re-open the theme manager.
Do you have a ~/.themes folder? Try renaming it as well.

---

### Post by Xian on 2005-03-20
Oh, and if you have libxcomposite installed try removing that package.

---

### Post by malegria on 2005-03-20
I've followed every one of your suggestions and I still face the same problem.

---

### Post by jkka on 2005-03-21
For me the problem is caused when composite extension is enabled on xorg.conf.

---

### Post by malegria on 2005-03-21
Now that I've restarted my computer, the problem is gone. Thanks for all your help.

---

### Post by malegria on 2005-03-21
The theme manager may be fixed, but no new icons still don't work. Any ideas?

---

### Post by jkka on 2005-03-22
Out of curiousity, did you have the composite extension on your xorg.conf?

---

