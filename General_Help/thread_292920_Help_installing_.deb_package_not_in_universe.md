---
title: "Help installing .deb package not in universe"
date: 2006-11-04
forum: General Help
---

### Post by edisav on 2006-11-04
Hi folks,

I'm not a Linux expert so I need some help installing an engineering application called Ngspice in my Dapper 6.06 (K)ubuntu box. 

Initially, I added universe to my sources file and searched for Ngspice with Adept Mgr. but nothing was found. However, I found the page below with all the info necessary to install Ngspice, but I'm not sure how to interpret and/or implement it.

[http://packages.ubuntu.com/hoary/electronics/ngspice](http://packages.ubuntu.com/hoary/electronics/ngspice)

So I downloaded the i386 ngspice_15-2_i386.deb package from the website, and I guess I'll have to use the "sudo dpkg -i ngspice_15-2_i386.deb" command to install the SW. 

Will this do it? Is there a better way? Can I use Adept Mgr.? Will there be conflicts between Dapper and Hoary?

Any help would be appreciated,
Thanks

---

### Post by 23meg on 2006-11-04
> Initially, I added universe to my sources file and searched for Ngspice with Adept Mgr. but nothing was found. Looks like that package was only available in Universe at the time of Hoary (the second version of Ubuntu) and was removed later. If its dependencies are installed, the *dpkg -i* command should do.

---

