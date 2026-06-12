---
title: "Unable to install libgdal1 because &quot;packages have unmet dependencies&quot;"
date: 2015-04-07
forum: General Help
---

### Post by nicolas37 on 2015-04-07
Hi, while trying to install postgis with postgresql-9.4 i got the following error:

```
The following packages have unmet dependencies:
 postgis : Depends: libgdal1 (>= 1.9.0) but it is not going to be installed
 postgresql-9.4-postgis-2.1 : Depends: libgdal1 (>= 1.9.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Therefore, i went on to install libgdal1. But i got the following:

```
The following packages have unmet dependencies:
 libgdal1 : Depends: libarmadillo2 (>= 2.4.2) but it is not installable
            Depends: libepsilon0 but it is not installable
            Depends: libhdf5-serial-1.8.4 but it is not installable or
                     libhdf5-1.8.4 but it is not installable
            Depends: libnetcdf6 but it is not installable
            Depends: libpoppler19 but it is not installable
            Depends: libspatialite3 (>= 2.4.0~rc2) but it is not installable
            Recommends: proj-bin but it is not going to be installed
```

Any ideas how to fix this? Im quite stucked.
Thanks in advance.

---

### Post by ian-weisser on 2015-04-07
One way to fix it is to remove the non-Ubuntu packages and dependencies, and to install postgis from the Ubuntu repositories.

Another way to fix it is to look at each of those dependencies with the 'apt-cache policy' command to discover why it's not installable. Maybe it's no longer available in the repos.
For example, libspatialite3 was dropped from Ubuntu after 12.04, replaced by libspatialite5.

---

### Post by Siddharth_Gupta on 2015-05-15
Can you please specify how to carry out these steps?

---

### Post by Siddharth_Gupta on 2015-05-15
> **ian-weisser said:**
> One way to fix it is to remove the non-Ubuntu packages and dependencies, and to install postgis from the Ubuntu repositories.

Another way to fix it is to look at each of those dependencies with the 'apt-cache policy' command to discover why it's not installable. Maybe it's no longer available in the repos.
For example, libspatialite3 was dropped from Ubuntu after 12.04, replaced by libspatialite5.

Can you please specify how to carry out these steps?

---

### Post by ian-weisser on 2015-05-15
Which steps do you need help with?
Which path do you intend to follow?
Do you have *exactly* the same problem as the nicolas37?

Are you asking for a primer on how to install and uninstall packages? Or how to identify dependencies? Or how to identify the source of a package? Or how to examine the dependencies of a package?

---

### Post by eoghan-n on 2015-10-08
Check that you don't have a /etc/apt/sources.list.d/pgdg.list installed (which doesn't match your distribution).  If you remove that file and do `apt-get update` you should be able to install from the main ubuntu repositories, or if that doesn't work, also try [https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS)

---

