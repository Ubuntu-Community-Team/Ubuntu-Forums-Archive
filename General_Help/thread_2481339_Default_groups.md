---
title: "Default groups"
date: 2022-11-26
forum: General Help
---

### Post by otyugh on 2022-11-26
Hey,
I've trouble making my scanner (PIXMA MG3600) using the official's drivers : [ScanGear MP v. 3.20 for Linux]("https://fr.canon.ch/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg3650.html?type=drivers&driverdetailid=tcm:109-1299580&os=linux%20%2864-bit%29&language=fr")
I wonder if it could be related to permissions ? I see I'm not part of group "scanner" (which exist on debian), could it be related to that or is it a Ubuntu 20.04 normal thing ? (oops I wanted to edit the subject title because it's not very explicit, but I can't T_T)


Default groups seem to be
> <USERNAME> adm cdrom sudo dip plugdev lpadmin lxd sambashare

Isn't there something missing ? Doing sane-find-scanner I get a "could no open USB device : Access denied (insufficient permission)

---

