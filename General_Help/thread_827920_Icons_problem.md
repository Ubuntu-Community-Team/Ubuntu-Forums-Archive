---
title: "Icons problem"
date: 2008-06-13
forum: General Help
---

### Post by t4ggs on 2008-06-13
Hi when I install a new icon package and use it I cant see the new icon set in things as folders....i.e. with this icons set:

Aero: [http://www.gnome-look.org/content/show.php/Aero?content=35437](http://www.gnome-look.org/content/show.php/Aero?content=35437)
Cherry-soda: [http://www.gnome-look.org/content/show.php/Cherry+Soda?content=14768](http://www.gnome-look.org/content/show.php/Cherry+Soda?content=14768)
Mac_OS_X_Leopadard_for_Ubuntu: 
OSX
Samui-2.0
Snow Apple


instead i see the default GNOME theme for folders icons.

im sure that the problem is not with the theme...

why is that??

---

### Post by bwang on 2008-06-13
The GNOME icon naming scheme was changed in the version that comes with Hardy. As a result, some icon sets will not work with Hardy.

---

### Post by t4ggs on 2008-06-13
thanks

---

### Post by BandD on 2008-06-14
You can fix it yourself though.  Just open up the icon theme you want to use and find the folder (or whatever icon you want to work) and make a link to it.  

Meanwhile, open up nautilus and navigate to /usr/share/icons/gnome/scalable/places (for the folder icon).  Make a file named after every file name you see in that dircetory for the icon you want.  You will probably have to do this through all the different sizes of the icon theme you want to work.

i.e.  if you have a file named stock_folder.png in the gnome directory but not in your desired icon theme, then link a file that IS the folder icon you want and name the link stock_folder.png (or .svg depending on the file type).  Do this for ALL files that exist in the gnome directory but not in your desired icon theme directory.

I hope that makes sense...

---

### Post by t4ggs on 2008-06-14
yeah it is understood thank u...but is a lot of work.

---

