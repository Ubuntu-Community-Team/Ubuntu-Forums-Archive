---
title: "xubuntu messed up desktop fonts"
date: 2016-07-25
forum: General Help
---

### Post by Chelidze on 2016-07-25
I am not sure when this happened but i think it happened either after i suspended the system or logged out of the system but after that i get broken desktop fonts, other fonts are fine 

here is a screen shot

 [ATTACH=CONFIG]270343[/ATTACH]

Does anyone knows how to fix this ??

---

### Post by Dennis N on 2016-07-25
I had the same problem on one of our computers, and it happened when using the Numix theme. I fixed it by changing the theme to Greybird (other themes will also be ok) and the problem was gone.

Another solution I read later (but didn't use) was to edit **/usr/share/themes/Numix/gtk-2.0/gtkrc** and change line 531 to read **textstyle = 0**

---

### Post by Chelidze on 2016-07-25
> **Dennis N said:**
> I had the same problem on one of our computers, and it happened when using the Numix theme. I fixed it by changing the theme to Greybird (other themes will also be ok) and the problem was gone.

Another solution I read later (but didn't use) was to edit **/usr/share/themes/Numix/gtk-2.0/gtkrc** and change line 531 to read **textstyle = 0**

Edited the line just like you suggested and it fixed my issue

---

