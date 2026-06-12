---
title: "Synaptic / apt messed up because of package inpropriety. . ."
date: 2014-07-09
forum: General Help
---

### Post by Richard Carlson on 2014-07-09
Qgis has screwed up my system . . . a plugin file for qgis has basically locked up synaptic and apt. I've tried to remove the application but haven't been successful as of yet. Any Idea's or helpful suggestions to correct this problem would be appreciated. 

```
root@richard-desktop:~# apt-get install qgis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 qgis : Depends: libqgis-analysis2.4.0 but it is not going to be installed
        Depends: libqgis-core2.4.0 but it is not going to be installed
        Depends: libqgis-gui2.4.0 but it is not going to be installed
        Depends: libqgis-networkanalysis2.4.0 but it is not going to be installed
        Depends: qgis-providers (= 2.4.0-0trusty1) but 2.0.1-2build2 is to be installed
        Depends: qgis-common (= 2.4.0-0trusty1) but 2.0.1-2build2 is to be installed
 qgis-plugin-globe : Depends: qgis (= 2.0.1-2build2) but 2.4.0-0trusty1 is to be installed
                     Depends: qgis-plugin-globe-common (= 2.0.1-2build2) but it is not going to be installed
 qgis-plugin-grass : Depends: qgis (= 2.0.1-2build2) but 2.4.0-0trusty1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@richard-desktop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libosgearth2 libosgearthannotation2 libosgearthfeatures2 libosgearthqt2
  libosgearthsymbology2 libosgearthutil2 libqgisgrass2.0.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgdal1h libosgearth3 libosgearthannotation3 libosgearthfeatures3
  libosgearthqt3 libosgearthsymbology3 libosgearthutil3 libqgis-analysis2.4.0
  libqgis-core2.4.0 libqgis-gui2.4.0 libqgis-networkanalysis2.4.0
  libqgisgrass2.4.0 osgearth-data qgis qgis-common qgis-plugin-globe
  qgis-plugin-globe-common qgis-plugin-grass qgis-plugin-grass-common
  qgis-providers qgis-providers-common
Suggested packages:
  openscenegraph
The following NEW packages will be installed:
  libosgearth3 libosgearthannotation3 libosgearthfeatures3 libosgearthqt3
  libosgearthsymbology3 libosgearthutil3 libqgis-analysis2.4.0
  libqgis-core2.4.0 libqgis-gui2.4.0 libqgis-networkanalysis2.4.0
  libqgisgrass2.4.0 osgearth-data qgis-plugin-globe-common                                                                                                                                                         
The following packages will be upgraded:                                                                                                                                                                           
  libgdal1h qgis qgis-common qgis-plugin-globe qgis-plugin-grass                                                                                                                                                   
  qgis-plugin-grass-common qgis-providers qgis-providers-common                                                                                                                                                    
8 upgraded, 13 newly installed, 0 to remove and 23 not upgraded.                                                                                                                                                   
1 not fully installed or removed.                                                                                                                                                                                  
Need to get 0 B/37.6 MB of archives.                                                                                                                                                                               
After this operation, 58.2 MB of additional disk space will be used.                                                                                                                                               
Do you want to continue? [Y/n] y                                                                                                                                                                                   
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 64896 package 'libtcl8.6:amd64':                                                                                                                      
 missing maintainer                                                                                                                                                                                                
dpkg: error: parsing file '/var/lib/dpkg/status' near line 64914 package 'qgis-plugin-globe-common':                                                                                                               
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@richard-desktop:~# 
```

This is the error messages I get in Konsole. I would prefer just to completely remove this whole package to get synaptic and apt once again to work properly. 


Thanks for any and all help. 

Richard :(

---

### Post by ian-weisser on 2014-07-09
1) Disable the PPA or non-Ubuntu repository you added to get a newer version of qgis.

2) Delete all qgis* packages from /var/cache/apt/archives

---

### Post by Richard Carlson on 2014-07-09
(synaptic:10494): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 64896 package 'libtcl8.6:amd64':
 missing maintainer
dpkg: error: parsing file '/var/lib/dpkg/status' near line 64914 package 'qgis-plugin-globe-common':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 64896 package 'libtcl8.6:amd64':
 missing maintainer
dpkg: error: parsing file '/var/lib/dpkg/status' near line 64914 package 'qgis-plugin-globe-common':
 missing version


I deleted the offending repository and went into var/cache/apt/archives and deleted the lines that made any reference to qgis. This is what I get when I re-run synaptic. . . .

---

### Post by ian-weisser on 2014-07-10
Good. That's a wholly different problem than an incompatible qgis PPA.

Replace the corrupt /var/lib/dpkg/status with the backup: /var/lib/dpkg/status-old

---

### Post by Richard Carlson on 2014-07-10
Thanks Ian. . . .your last comment fixed the issue by replacing the status with status-old. I was really starting to panic because nothing I did with Synaptic or apt would allow me to get rid of the file or even all of the associated app files. Saves me a great deal of work about rethinking a re-install altogether. . . I'm not new to Linux or Ubuntu but haven't really played with the intricacies of fixing issues that sometime arise with 'broken' files etc. I'm once again a happy camper. 


Richard ;)

---

