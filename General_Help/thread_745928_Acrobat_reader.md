---
title: "Acrobat reader"
date: 2008-04-05
forum: General Help
---

### Post by bennyda on 2008-04-05
I have installed Acrobat Reader recently on Ubuntu 7.04. While it appears in the Applications drop-down list it does not show in the "Open With..." lists.

I am unable to get OpenOffice to list Windows fonts, such as Century Gothic, Times New Roman etc.

---

### Post by forestpixie on 2008-04-05
Right click a pdf - open with other - use custom command - navigate to /usr/bin - acrobat should be there. If you want them to always open with acrobat - instead right click and then properties - open with - navigate to /usr/bin and find acrobat.

Assuming that you have msttcorefonts installed - it comes with ubuntu-restricted-extras - or fonts in your home folder - have you run sudo fc-cache -f -v to update the fonts.

---

