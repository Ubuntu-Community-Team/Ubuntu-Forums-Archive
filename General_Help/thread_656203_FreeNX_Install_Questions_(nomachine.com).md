---
title: "FreeNX Install Questions (nomachine.com)"
date: 2008-01-02
forum: General Help
---

### Post by m i k e on 2008-01-02
After Installing the client from nomachine.com I got this message:

```
CUPS Printing Backend

 The NX Client set-up procedure detected that your "IPP CUPS" printing
 backend doesn't allow printing from the NX session. In order to have
 printing support in your NX system, you need to set proper permissions
 on the IPP backend. Please execute:

   chmod 755 /usr/lib/cups/backend/ipp

```
1.  What does that mean?

After installing the node from nomachine.com I got this message:

```
CUPS Printing Backend

 The NX Node setup procedure could not detect your "CUPS"
 installation: either CUPS  is not installed on your system
 or it was installed in a non-standard path. CUPS is needed
 in order to enable printing support in your NX system.
 Please note that you can enable  printing support for your
 NX system at any time; to do this make sure  that you have
 CUPS installed then run:

   /usr/NX/scripts/setup/nxnode --nxprintsetup <pathname>

 to specify the location of the CUPS root path. 
NX> 700 Bye.
```
2.  What does that mean?

Thanks for any help.

---

### Post by m i k e on 2008-01-02
bump.

---

