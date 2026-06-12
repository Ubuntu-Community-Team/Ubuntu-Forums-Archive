---
title: "Wubi support triple or quad boot?"
date: 2008-06-25
forum: General Help
---

### Post by Jeconti on 2008-06-25
I'm a Linux enthusiast that doesn't really know the first thing about the operating system, but I've been trying out various distributions on older computers that float my way now and then.

I used Wubi to install Ubuntu on my main computer and am happy to report it's working perfectly.

So my questions are as follows:

1) What the hell did I just do? Where does it exist on the drive? Can either OS see the files from the other on the drive? There's only one partition so shouldn't the files for both be there?

2) Since it's working so well, I'd like to try out the KDE beta as well as Edubuntu at some point. Can Wubi set up for more than just dual boot? Can I install both and see them work?

Thanks.

---

### Post by Mark Gyver on 2008-06-25
> Where does it exist on the drive? Can either OS see the files from the other on the drive? There's only one partition so shouldn't the files for both be there?
The Ubuntu install should be contained in a couple files in *C:\ubuntu\*.  Specifically, the Ubuntu files are contained within the file *C:\ubuntu\disks\root.disk* which is used as a virtual partition.  I don't know how (or if) to see Ubuntu's files from within Windows, but you should be able to see (and change) you Windows files from Ubuntu by going to */host/*.  I'm a bit unsure about the locations of the files in Windows, but it should at least be similar to the above.

> Since it's working so well, I'd like to try out the KDE beta as well as Edubuntu at some point. Can Wubi set up for more than just dual boot? Can I install both and see them work?
I'm not sure if Wubi's able to handle multiple installs like that, but there's an easier way to try a different *buntu.  Just open your package manager of choice, do a search for packages with *desktop* in their name and install whichever package you need from there.

*edubuntu-desktop* gives you Edubuntu, *kubuntu-kde4-desktop* gives you the new version of KDE, *kubuntu-desktop* gives you the stable version of KDE, *ubuntu-desktop* (which you probably already have) gives you Ubuntu's default desktop environment (Gnome), and *xubuntu-desktop* gives you XFCE.  

You can install is many of the above as you wish and select which desktop environment to run at the login prompt.  Also, you can usually run programs from one environment from the others.  Experiment to find the one that best suits your needs.

Note: *while Kubuntu, Ubuntu, and Xubuntu packages mainly provide their distinct desktop environments and corresponding sets of programs, Edubuntu is more about a set of educational programs than the desktop environment so it has multiple **buntu-desktop* packages to choose from.*

---

