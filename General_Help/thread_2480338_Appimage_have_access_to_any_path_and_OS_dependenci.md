---
title: "Appimage have access to any path and OS dependencies ?"
date: 2022-10-26
forum: General Help
---

### Post by aug7744 on 2022-10-26
Hello.

Appimage start loading software and dependencies from inside appimage file.
Some softwares have appimage version ( GIMP , Kdenlive , Scribus and etc ) and have support for plugins.
The same softwares being installed using deb files have correct access to plugins and others files paths.

Appimage allow software access to OS paths and libraries dependencies ?
Appimage create an virtual fs where only will be loaded files from Appimage file ?

Thanks for reading.

---

### Post by grahammechanical on 2022-10-26
> Appimage allow software access to OS paths and libraries dependencies ?
Appimage create an virtual fs where only will be loaded files from Appimage file ?

In my opinion the best people to answer those questions would be the developers of the AppImage concept.

[https://appimage.org/](https://appimage.org/)

The publicity says this:

> The key idea of the AppImage format is **one app = one file**. Every  AppImage contains an app and all the files the app needs to run. In  other words, each AppImage has no dependencies other than what is  included in the targeted base operating system(s).

That seems to say that the application can access OS paths and libraries.

To be fair the publicity also says this:

> Download an application, make it executable, and run! No  need to install. No system libraries or system preferences are altered.                               Can also run in a sandbox like [Firejail]("https://github.com/netblue30/firejail")                      

That last comment about running in a sandbox is of interest to anyone who would prefer applications to have no or limited access to OS paths and libraries.

Regards

---

