---
title: "PostGIS in Hardy"
date: 2008-05-06
forum: General Help
---

### Post by Go_Bucks on 2008-05-06
Note to all users of postgresql-8.2-postgis in hardy... I was appalled when all of my GIS programs crashed after my hardy upgrade when trying to load a postgis layer. What I discovered was that they all use liblwgeom.so.1.2 and that library has been replaced with liblwgeom.so.1.3 in hardy. The fix is to create a symlink named liblwgeom.so.1.2 linked to liblwgeom.so.1.3.

---

### Post by talgise on 2008-05-19
> **Go_Bucks said:**
> Note to all users of postgresql-8.2-postgis in hardy... I was appalled when all of my GIS programs crashed after my hardy upgrade when trying to load a postgis layer. What I discovered was that they all use liblwgeom.so.1.2 and that library has been replaced with liblwgeom.so.1.3 in hardy. The fix is to create a symlink named liblwgeom.so.1.2 linked to liblwgeom.so.1.3.

System:
Unbutu 8.04 Server
postgresql-8.3
geos-3.0.0
proj4 4.6.0
gdal 1.4.4

trying to install postgis-1.2.1.
This is my errors:
"lwgeom_geos_c.c:2438"
"make[1] : *** [lwgeom_geos_c.o] Error"

can someone please help?

---

### Post by Go_Bucks on 2008-05-21
> **talgise said:**
> System:
Unbutu 8.04 Server
postgresql-8.3
geos-3.0.0
proj4 4.6.0
gdal 1.4.4

trying to install postgis-1.2.1.
This is my errors:
"lwgeom_geos_c.c:2438"
"make[1] : *** [lwgeom_geos_c.o] Error"

can someone please help?

Are you installing from source or the repos? The version of postgis in the repos is 1.3.3. I am not sure 1.2.1 even works with Postgres 8.3.

---

