---
title: "hpijs driver"
date: 2014-12-10
forum: General Help
---

### Post by trav9595 on 2014-12-10
I was trying to find driver co-file hpijs in the software  but no luck???  Does anyone know where it is???

---

### Post by tgalati4 on 2014-12-11
You probably want *hplip*.  *hpijs* is for the really old HP inkjet printers.

> tgalati4@Mint14-Extensa ~ $ apt-cache search hpijs
hpijs - transitional dummy package for hpijs printer driver
hplip - HP Linux Printing and Imaging System (HPLIP)
hplip-dbg - HP Linux Printing and Imaging - debugging information
hplip-doc - HP Linux Printing and Imaging - documentation
libijs-0.35 - IJS raster image transport protocol: shared library
libijs-dev - IJS raster image transport protocol: development files
printer-driver-hpijs - HP Linux Printing and Imaging - gs IJS driver (hpijs)
printer-driver-pxljr - printer driver for HP Color LaserJet 35xx/36xx
hpijs-ppds - HP Linux Printing and Imaging - HPIJS PPD files


---

### Post by oldfred on 2014-12-11
If a newer HP printer you may need the version directly from HP, as the version in the repository is often several versions old.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

