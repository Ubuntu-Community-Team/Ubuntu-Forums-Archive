---
title: "openoffice icons dissappear and reappear in gnome o.O"
date: 2007-02-26
forum: General Help
---

### Post by 9a3eedi on 2007-02-26
I use kubuntu, and I installed gnome through apt-get.

So then I switched to gnome because apparently it works best with beryl.

When I run openoffice, I see that the icons disappear and then reappear when I mouse over them

here's a picture to explain it further

[http://i5.photobucket.com/albums/y156/9a3eedi/SUSE/Openofficec.png](http://i5.photobucket.com/albums/y156/9a3eedi/SUSE/Openofficec.png)

This doesn't happen in KDE or in fluxbox. I'm puzzled as to why this happens here o.O


I'm using kubuntu on edgy x86 on a centrino

---

### Post by 9a3eedi on 2007-02-27
bump.

Does the fact that I use beryl/XGL have anything to do with this?

---

### Post by froghopper on 2007-02-27
I had this problem once before. I think required an update of openoffice.org-gnome.

Unfortunately I just loaded writer and my icons were completely gone :-( So I upgraded to the latest openoffice 2.1.4 but it did not help. Uninstalling and reinstalling did fix the problem. It seems to be a problem reported here and there but with no definite resolution. Good luck.

---

### Post by erdalronahi on 2007-03-04
I am having this problem in Edgy, too. Icons and menus disappear and become unreadable. It makes OpenOffice.org unusable. 

However uninstalling did not help at all. I uninstalled and even purged all OpenOffice.org-related packages as well as GNOME. Not using Beryl does not help either.

---

### Post by FrankN on 2007-03-20
I found a solution on-line and it did work for me:
[http://www.oooforum.org/forum/viewtopic.phtml?p=182685]("http://www.oooforum.org/forum/viewtopic.phtml?p=182685")

---

### Post by 9a3eedi on 2007-03-20
> 

Do you have the gtk2-engines-gtk-qt package installed ?
It seems this is the root cause but I'm not 100% sure of it. Removing it has solved the issue for some.


Why do I get this feeling that if I remove this package 40% of my apps will stop working?

the way it is named.. it sounds so............ essential o.o

anyways, thanks for the suggested solution. I'll try it out, and will come back for the results..

---

