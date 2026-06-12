---
title: "Problems after installing MapGuide"
date: 2017-03-19
forum: General Help
---

### Post by Achilles124 on 2017-03-19
I have installed MapGuide by way of the script: mginstallubuntu.sh. This can be found here: [http://trac.osgeo.org/mapguide/wiki/Release/2.6/Notes](http://trac.osgeo.org/mapguide/wiki/Release/2.6/Notes).

Things have not gone as planned. I get a software notification that the installed package has unmet dependencies. I ran sudo apt-get update && sudo apt-get upgrade.
And I get this:
Hit:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) yakkety InRelease
Hit:2 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) yakkety-updates InRelease
Hit:3 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) yakkety-backports InRelease          
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease             
Reading package lists... Done                                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fdo-gdal:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-ogr:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-sdf:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-shp:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-sqlite:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-wfs:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
 fdo-wms:i386 : Depends: libcurl3:i386 (>= 7.16.2-1) but it is not installed
E: Unmet dependencies. Try using -f.

**Question:** is it a good idea to install with force (-f)? What can be the downside?

---

