---
title: "OpenOffice.org not starting"
date: 2008-06-23
forum: General Help
---

### Post by adityavpratap on 2008-06-23
Hi,
I am running Ubuntu 8.04 on my Acer Aspire 5100 laptop.
Since yesterday I am unable to get OpenOffice to start. The OpenOffice.org splash is momentarily displayed and then it disappears. swriter at the command prompt gives the following error message -
> 
 /usr/lib/openoffice/program/soffice.bin.bin: error while loading shared libraries: libucbhelper3gcc3.so: cannot open shared object file: No such file or directory


whereas a listing of the /usr/lib/openoffice/program/ folder reveals the existence of libucbhelper4gcc3.so.

Any idea how I can set right the problem?

---

### Post by Thanoulis on 2008-06-23
I had exactly the same problem. It solved by removing the openoffice-gnome and openoffice-gtk packages. Now it starts normally, but it does not ally with my gtk theme..i can live with that, though...

---

### Post by adityavpratap on 2008-06-23
Okay, I tried removing openoffice.org-gnome & openoffice.org-gtk but I still I get the same error message

---

