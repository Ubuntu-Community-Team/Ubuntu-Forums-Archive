---
title: "NX Client Repository in Edgy"
date: 2007-01-05
forum: General Help
---

### Post by useResa on 2007-01-05
Hi,

In the "old Dapper days" I have installed NX client on my laptop simply by using Synaptics. However, after my upgrade to Edgy, the repositories don't have the NX client available anymore.

When I try to mark it for installation I get the following message:
> Package nxclient has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Please also see attached screenshot of the search result for *nxclient* in Synaptics.

Could anyone help me how I can get nxclient installed via Synaptics
(I know I can do it also by downloading from [nomachine](http://www.nomachine.com), but I found it convenient that I could also use Synaptics).

---

### Post by behemot on 2007-01-05
Currently there is no edgy repos for FreeNX.
Seveas hosts verson compatible with dapper.

Linux Terminal Server may soon release debs for edgy.
You can read more at:

[http://www.2x.com/](http://www.2x.com/)

If you find it inconvenient to install debs using apt-get then you may consider installing gdebi package.

---

### Post by useResa on 2007-01-05
> **behemot said:**
> Currently there is no edgy repos for FreeNX.
Seveas hosts verson compatible with dapper.
Thank you for clarifying this

> **behemot said:**
>  Linux Terminal Server may soon release debs for edgy.
You can read more at:

[http://www.2x.com/](http://www.2x.com/)

This is similar to NX from what I understand

> **behemot said:**
>  If you find it inconvenient to install debs using apt-get then you may consider installing gdebi package.
Thank you for pointing this package out to me.
Downloaded the deb from nomachine.com and the installation ran without problems using gdebi.   :-D

---

