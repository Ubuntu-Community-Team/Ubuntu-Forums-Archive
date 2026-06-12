---
title: "Some applications do not change appearances when the Emerald theme changes?"
date: 2008-01-03
forum: General Help
---

### Post by chunchengch on 2008-01-03
I download and install a new Emerald theme, all the appearances of applications change except the Opera, OpenOffice and Synaptic, I am not sure it is a problem, if it is, how can I fix it? thanks a lot!

[ATTACH]55116[/ATTACH]

[ATTACH]55117[/ATTACH]

---

### Post by chunchengch on 2008-01-03
[attach]55118[/attach]

---

### Post by kpkeerthi on 2008-01-03
It looks like you applied a GTK theme. 

Synaptic did not take it because it is running as a 'root' application. (There is a post some where in the forum on how to 'theme' root application. Unfortunately, I dont remember where. Try search for yourself. Sorry.)

Opera just ignored the theme because it is not a GTK application. Its based on QT.

---

### Post by staticvoid on 2008-01-03
you can get qt themes at kde-look.org

---

### Post by chunchengch on 2008-01-03
Thanks a lot!

I learn one more thing about Linux.

---

### Post by chunchengch on 2008-01-03
I have changed the theme of root applications, but how can I change the theme of OpenOffice?
thanks!

---

### Post by chunchengch on 2008-01-04
I finally find the solution to coincide the the theme of Openoffice with Gnome, just need to install packages openoffice.org-gnome and openoffice.org-gtk.

I am using a new dark GTK theme, the first time I install these packages, I forget to save the original color setting of Openoffice, so when I open an old .odt or .ods file, I have to change some font colors to make document more visible, because the background is dark now, and it is white before.

However, it is really inconvenient and impossible to convert all the old files, so I remove these two packages and save the original color setting of Openoffice, then I re-install these two packages, now the Openoffice Word Processor display document normally, but the Openoffice Spreadsheet does not, all the colors of fonts and backgrounds are messed, and I can not change it, here are screenshots for your reference, and hope there is solution for this problem, thanks a lot!

 [ATTACH]55255[/ATTACH]    (default)

[ATTACH]55256[/ATTACH]     (themed)

[ATTACH]55257[/ATTACH]     (color setting saved)

---

### Post by bn127 on 2008-01-05
Hi!

For the management tools like Synaptic adopting the same visual as the other windows you change your themes from ~/.themes (.themes is a hidden folder) to /usr/share/themes. Concerning the Openoffice issues I'm sorry but I can't help you.

Regards.

---

