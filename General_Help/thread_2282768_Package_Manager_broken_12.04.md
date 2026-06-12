---
title: "Package Manager broken 12.04"
date: 2015-06-16
forum: General Help
---

### Post by j0eb0b on 2015-06-16
I tried to update a friend's computer that hasn't been updated in a while.  I got an error there are a bunch of packages with dependencies.

I ran sudu dpkg -- configure - a and this is what I got:

```
  Errors were encountered while processing:
 libqt4-dbus
 qdbus
 libqt4-xml
 libqt4-xml:i386
 libqt4-network
 libqt4-script
 libqt4-dbus:i386
 libqt4-designer:i386
 libqt4-qt3support:i386
 libqt4-xmlpatterns
 libqt4-declarative
 libqt4-network:i386
 libqt4-script:i386
 libqt4-scripttools:i386
 libqt4-xmlpatterns:i386
 libqtgui4
 libqt4-declarative:i386
 libqt4-svg
 libqt4-opengl
 libqtgui4:i386
 libqt4-svg:i386
 libqt4-opengl:i386
```


How do I fix this?

---

### Post by ventrical on 2015-06-16
Try this:

```

sudo apt-get -f install

```

Regards..

---

### Post by j0eb0b on 2015-06-16
I tried that and here is what happens:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-65-generic linux-headers-3.2.0-29 linux-headers-3.2.0-60
  linux-headers-3.2.0-61 linux-headers-3.2.0-57 linux-headers-3.2.0-63
  linux-headers-3.2.0-58 linux-headers-3.2.0-64 linux-headers-3.2.0-59
  linux-headers-3.2.0-65 linux-headers-3.2.0-67 linux-headers-3.2.0-80
  linux-headers-3.2.0-75 linux-headers-3.2.0-82 linux-headers-3.2.0-77
  linux-headers-3.2.0-79 linux-headers-3.2.0-29-generic
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-63-generic
  linux-headers-3.2.0-58-generic linux-headers-3.2.0-79-generic
  linux-headers-3.2.0-61-generic linux-headers-3.2.0-82-generic
  linux-headers-3.2.0-77-generic linux-headers-3.2.0-64-generic
  linux-headers-3.2.0-59-generic libtommath0 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-80-generic linux-headers-3.2.0-75-generic
  linux-headers-3.2.0-57-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-xml
The following packages will be upgraded:
  libqt4-xml
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
22 not fully installed or removed.
Need to get 0 B/95.3 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libqt4-xml (--configure):
 libqt4-xml:amd64 4:4.8.1-0ubuntu4.8 cannot be configured because libqt4-xml:i386 is in a different version (4:4.8.1-0ubuntu4.9)
dpkg: error processing libqt4-xml:i386 (--configure):
 libqt4-xml:i386 4:4.8.1-0ubuntu4.9 cannot be configured because libqt4-xml:amd64 is in a different version (4:4.8.1-0ubuntu4.8)
dpkg: dependency problems prevent configuration of libqt4-dbus:
 libqt4-dbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already

dpkg: error processing libqt4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qdbus:
 qdbus depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
 qdbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.
dpkg: error processing qdbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:i386:
 libqt4-dbus:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-dbus:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:i386:
 libqt4-network:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus:i386 is not configured yet.
dpkg: error processing libqt4-network:i386 (--conNo apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       figure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:
 libqt4-network depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:i386:
 libqt4-script:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus:i386 is not configured yet.
dpkg: error processing libqt4-script:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:i386:
 libqt4-xmlpatterns:No apport report written because MaxReports is reached already
  i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:
 libqt4-xmlpatterns depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network is not configured yet.
dpkg: error processing libqt4-xmlpatterns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
 libqt4-declarative:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
 libqt4-declarative:i386 depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xmlpatterns:i386 is not configured yet.
dpkg: error processing libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network is not configured yet.
 libqt4-declarative depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script is not configured yet.
 libqt4-declarative depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xmlpatterns is not configured yet.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:
 libqt4-designer:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
 libqt4-designer:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-designer:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:i386:
 libqt4-qt3support:i386 depends on libqt4-designer (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-designer:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-qt3support:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-scripttools:i386:
 libqt4-scripttools:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
dpkg: error processing libqt4-scripttools:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-declarative:i386 is not configured yet.
dpkg: error processing libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-declarative is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
 libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-opengl:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:i386:
 libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-svg:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-xml
 libqt4-xml:i386
 libqt4-dbus
 qdbus
 libqt4-dbus:i386
 libqt4-network:i386
 libqt4-network
 libqt4-script:i386
 libqt4-script
 libqt4-xmlpatterns:i386
 libqt4-xmlpatterns
 libqt4-declarative:i386
 libqt4-declarative
 libqt4-designer:i386
 libqt4-qt3support:i386
 libqt4-scripttools:i386
 libqtgui4:i386
 libqtgui4
 libqt4-opengl
 libqt4-opengl:i386
 libqt4-svg
 libqt4-svg:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2015-06-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by j0eb0b on 2015-06-16
Sorry let me try this again.  The output I get when I run 
```
sudo apt-get - F install is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-65-generic linux-headers-3.2.0-29 linux-headers-3.2.0-60
  linux-headers-3.2.0-61 linux-headers-3.2.0-57 linux-headers-3.2.0-63
  linux-headers-3.2.0-58 linux-headers-3.2.0-64 linux-headers-3.2.0-59
  linux-headers-3.2.0-65 linux-headers-3.2.0-67 linux-headers-3.2.0-80
  linux-headers-3.2.0-75 linux-headers-3.2.0-82 linux-headers-3.2.0-77
  linux-headers-3.2.0-79 linux-headers-3.2.0-29-generic
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-63-generic
  linux-headers-3.2.0-58-generic linux-headers-3.2.0-79-generic
  linux-headers-3.2.0-61-generic linux-headers-3.2.0-82-generic
  linux-headers-3.2.0-77-generic linux-headers-3.2.0-64-generic
  linux-headers-3.2.0-59-generic libtommath0 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-80-generic linux-headers-3.2.0-75-generic
  linux-headers-3.2.0-57-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-xml
The following packages will be upgraded:
  libqt4-xml
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
22 not fully installed or removed.
Need to get 0 B/95.3 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libqt4-xml (--configure):
 libqt4-xml:amd64 4:4.8.1-0ubuntu4.8 cannot be configured because libqt4-xml:i386 is in a different version (4:4.8.1-0ubuntu4.9)
dpkg: error processing libqt4-xml:i386 (--configure):
 libqt4-xml:i386 4:4.8.1-0ubuntu4.9 cannot be configured because libqt4-xml:amd64 is in a different version (4:4.8.1-0ubuntu4.8)
dpkg: dependency problems prevent configuration of libqt4-dbus:
 libqt4-dbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already

dpkg: error processing libqt4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qdbus:
 qdbus depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
 qdbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.
dpkg: error processing qdbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:i386:
 libqt4-dbus:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-dbus:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:i386:
 libqt4-network:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus:i386 is not configured yet.
dpkg: error processing libqt4-network:i386 (--conNo apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       figure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:
 libqt4-network depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:i386:
 libqt4-script:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus:i386 is not configured yet.
dpkg: error processing libqt4-script:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:i386:
 libqt4-xmlpatterns:No apport report written because MaxReports is reached already
  i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:
 libqt4-xmlpatterns depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network is not configured yet.
dpkg: error processing libqt4-xmlpatterns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
 libqt4-declarative:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
 libqt4-declarative:i386 depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xmlpatterns:i386 is not configured yet.
dpkg: error processing libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network is not configured yet.
 libqt4-declarative depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script is not configured yet.
 libqt4-declarative depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xmlpatterns is not configured yet.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:
 libqt4-designer:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
 libqt4-designer:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-designer:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:i386:
 libqt4-qt3support:i386 depends on libqt4-designer (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-designer:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-network:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-xml:i386 is not configured yet.
dpkg: error processing libqt4-qt3support:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-scripttools:i386:
 libqt4-scripttools:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-script:i386 is not configured yet.
dpkg: error processing libqt4-scripttools:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-declarative:i386 is not configured yet.
dpkg: error processing libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
  Package libqt4-declarative is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
 libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-opengl:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:i386:
 libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-svg:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-xml
 libqt4-xml:i386
 libqt4-dbus
 qdbus
 libqt4-dbus:i386
 libqt4-network:i386
 libqt4-network
 libqt4-script:i386
 libqt4-script
 libqt4-xmlpatterns:i386
 libqt4-xmlpatterns
 libqt4-declarative:i386
 libqt4-declarative
 libqt4-designer:i386
 libqt4-qt3support:i386
 libqt4-scripttools:i386
 libqtgui4:i386
 libqtgui4
 libqt4-opengl
 libqt4-opengl:i386
 libqt4-svg
 libqt4-svg:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2015-06-16
Please refer to post 4 again for directions on using code tags.
Thanks

---

### Post by j0eb0b on 2015-06-16
One more time.

The output I get when I run sudo apt-get - F install is:

```

    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... Done
    The following packages were automatically installed and are no longer required:
      linux-headers-3.2.0-65-generic linux-headers-3.2.0-29 linux-headers-3.2.0-60
      linux-headers-3.2.0-61 linux-headers-3.2.0-57 linux-headers-3.2.0-63
      linux-headers-3.2.0-58 linux-headers-3.2.0-64 linux-headers-3.2.0-59
      linux-headers-3.2.0-65 linux-headers-3.2.0-67 linux-headers-3.2.0-80
      linux-headers-3.2.0-75 linux-headers-3.2.0-82 linux-headers-3.2.0-77
      linux-headers-3.2.0-79 linux-headers-3.2.0-29-generic
      linux-headers-3.2.0-60-generic linux-headers-3.2.0-63-generic
      linux-headers-3.2.0-58-generic linux-headers-3.2.0-79-generic
      linux-headers-3.2.0-61-generic linux-headers-3.2.0-82-generic
      linux-headers-3.2.0-77-generic linux-headers-3.2.0-64-generic
      linux-headers-3.2.0-59-generic libtommath0 linux-headers-3.2.0-67-generic
      linux-headers-3.2.0-80-generic linux-headers-3.2.0-75-generic
      linux-headers-3.2.0-57-generic
    Use 'apt-get autoremove' to remove them.
    The following extra packages will be installed:
      libqt4-xml
    The following packages will be upgraded:
      libqt4-xml
    1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
    22 not fully installed or removed.
    Need to get 0 B/95.3 kB of archives.
    After this operation, 1,024 B of additional disk space will be used.
    Do you want to continue [Y/n]? y
    dpkg: error processing libqt4-xml (--configure):
     libqt4-xml:amd64 4:4.8.1-0ubuntu4.8 cannot be configured because libqt4-xml:i386 is in a different version (4:4.8.1-0ubuntu4.9)
    dpkg: error processing libqt4-xml:i386 (--configure):
     libqt4-xml:i386 4:4.8.1-0ubuntu4.9 cannot be configured because libqt4-xml:amd64 is in a different version (4:4.8.1-0ubuntu4.8)
    dpkg: dependency problems prevent configuration of libqt4-dbus:
     libqt4-dbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
      Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already

    dpkg: error processing libqt4-dbus (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of qdbus:
     qdbus depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-dbus is not configured yet.
     qdbus depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
      Version of libqt4-xml on system is 4:4.8.1-0ubuntu4.8.
    dpkg: error processing qdbus (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-dbus:i386:
     libqt4-dbus:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-xml:i386 is not configured yet.
    dpkg: error processing libqt4-dbus:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-network:i386:
     libqt4-network:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-dbus:i386 is not configured yet.
    dpkg: error processing libqt4-network:i386 (--conNo apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           figure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-network:
     libqt4-network depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-dbus is not configured yet.
    dpkg: error processing libqt4-network (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-script:i386:
     libqt4-script:i386 depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-dbus:i386 is not configured yet.
    dpkg: error processing libqt4-script:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-script:
     libqt4-script depends on libqt4-dbus (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-dbus is not configured yet.
    dpkg: error processing libqt4-script (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:i386:
     libqt4-xmlpatterns:No apport report written because MaxReports is reached already
      i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-network:i386 is not configured yet.
    dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:
     libqt4-xmlpatterns depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-network is not configured yet.
    dpkg: error processing libqt4-xmlpatterns (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
     libqt4-declarative:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-network:i386 is not configured yet.
     libqt4-declarative:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-script:i386 is not configured yet.
     libqt4-declarative:i386 depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-xmlpatterns:i386 is not configured yet.
    dpkg: error processing libqt4-declarative:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-declarative:
     libqt4-declarative depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-network is not configured yet.
     libqt4-declarative depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-script is not configured yet.
     libqt4-declarative depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-xmlpatterns is not configured yet.
    dpkg: error processing libqt4-declarative (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-designer:i386:
     libqt4-designer:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-script:i386 is not configured yet.
     libqt4-designer:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-xml:i386 is not configured yet.
    dpkg: error processing libqt4-designer:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-qt3support:i386:
     libqt4-qt3support:i386 depends on libqt4-designer (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-designer:i386 is not configured yet.
     libqt4-qt3support:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-network:i386 is not configured yet.
     libqt4-qt3support:i386 depends on libqt4-xml (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-xml:i386 is not configured yet.
    dpkg: error processing libqt4-qt3support:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-scripttools:i386:
     libqt4-scripttools:i386 depends on libqt4-script (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-script:i386 is not configured yet.
    dpkg: error processing libqt4-scripttools:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqtgui4:i386:
     libqtgui4:i386 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-declarative:i386 is not configured yet.
    dpkg: error processing libqtgui4:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqtgui4:
     libqtgui4 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.9); however:
      Package libqt4-declarative is not configured yet.
    dpkg: error processing libqtgui4 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-opengl:
     libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
      Package libqtgui4 is not configured yet.
    dpkg: error processing libqt4-opengl (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
     libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
      Package libqtgui4:i386 is not configured yet.
    dpkg: error processing libqt4-opengl:i386 (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-svg:
     libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
      Package libqtgui4 is not configured yet.
    dpkg: error processing libqt4-svg (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of libqt4-svg:i386:
     libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.9); however:
      Package libqtgui4:i386 is not configured yet.
    dpkg: error processing libqt4-svg:i386 (--configure):
     dependency problems - leaving unconfigured
    Errors were encountered while processing:
     libqt4-xml
     libqt4-xml:i386
     libqt4-dbus
     qdbus
     libqt4-dbus:i386
     libqt4-network:i386
     libqt4-network
     libqt4-script:i386
     libqt4-script
     libqt4-xmlpatterns:i386
     libqt4-xmlpatterns
     libqt4-declarative:i386
     libqt4-declarative
     libqt4-designer:i386
     libqt4-qt3support:i386
     libqt4-scripttools:i386
     libqtgui4:i386
     libqtgui4
     libqt4-opengl
     libqt4-opengl:i386
     libqt4-svg
     libqt4-svg:i386
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

