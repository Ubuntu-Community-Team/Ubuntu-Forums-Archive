---
title: "[SOLVED] how to uninstall applications installed using sudo dpkg -i --force-all"
date: 2008-06-06
forum: General Help
---

### Post by mghambunan on 2008-06-06
I installed 32bit Gizmo Project package in a 64bit ubuntu hardy using the sudo dpkg -i --force-all command. After installation I encountered problems running the application and planning to remove it but can't find the package in synaptic package manager.

Installation details:
1. I downloaded and installed the getlibs application from this site: [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
2. I downloaded the 32bit .deb package of Gizmo Project from [http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb) to my desktop.
3. sudo dpkg -i --force-all Desktop/gizmo-project_3.1.0.79_libstdc++6_i386.deb
4. sudo cp /usr/lib/libsipphoneapi.so.1.7.07.73 /usr/lib32

Any help is highly appreciated.

---

### Post by sdennie on 2008-06-06
You could try looking for the package with

```

dpkg -l | grep gizmo

```

It's almost certainly called gizmo-project so, to remove it:

```

sudo apt-get remove gizmo-project

```

It should be safe to remove the .so you put in /usr/lib32 but, to be sure, run this first:

```

dpkg -S /usr/lib32/libsipphoneapi.so.1.7.07

```

It should be fine to remove it if it comes back with:

```

dpkg: /usr/lib32/libsipphoneapi.so.1.7.07 not found.

```

---

### Post by iaculallad on 2008-06-06
You could also try:

```
sudo dpkg --purge getlibs-all
sudo dpkg --purge gizmo-project
```

---

### Post by mghambunan on 2008-06-06
Thank you guys for the help. I Manage to uninstall the application using ```
sudo dpkg --remove gizmo-project
```

Thanks again guys for responding to my post.

---

### Post by Cappy on 2008-06-08
If it wouldn't run because it was missing libraries then you would need to use
```
sudo getlibs /usr/bin/gizmo
```
(that may not be the right path; it may be /usr/bin/gizmo-project or something)

---

