---
title: "When the software is updated in the repositories?"
date: 2018-08-16
forum: General Help
---

### Post by enricobe on 2018-08-16
Hello,
repositories, "Software" app and apt-get are really useful to get all the programs updated, but I noticed that a lot of programs are not really updated.


E.g. in Ubuntu 18.04 you can find:
calibre 3.21 (06 Apr 2018). The last version avalible on the website is 3.29
qbittorrent 4.0.3 (17 Dec 2017).  The last version avalible on the website is 4.1.2


I'm aware that not all the software can be updated in some days, but who manages the software updates in the official repositories and why some apps are so old?

---

### Post by mörgæs on 2018-08-16
Never (as a rule of thumb - a few exceptions exist). 

When a new Buntu release (18.10 as of now) is in development new releases of the contributing software, say Calibre, are pulled in.

Security bug fixes are added to 18.04, not new functionality.

---

### Post by enricobe on 2018-08-16
> **mörgæs said:**
> Never (as a rule of thumb - a few exceptions exist). 

When a new Buntu release (18.10 as of now) is in development new releases of the contributing software, say Calibre, are pulled in.

Security bug fixes are added to 18.04, not new functionality.

Hello. I can't understand why some new releases are not included. calibre has an April release, while qBittorrent february release isn't included. 
I would prefer to receive regulary updates and not only when a new OS version is released, but this is not a big problem.

---

### Post by mörgæs on 2018-08-16
Then you have to look for a 'rolling release' distro or use a PPA.

If all new software were backported to 18.04 then 18.04 and 18.10 would essentially be same release.

---

### Post by wyliecoyoteuk on 2018-08-16
Each new application has to be tested against the main Distro's other packages, Kernel, etc. which is why bugfixes are added, but not new whole releases.
New releases may need new versions of libraries also used by other packages, and updating those may break other packages.Testing for this can be time consuming.
You must remember that many of the maintainers are volunteers who would rather be working on the next release.
If you want the newest versions of a package, see if it is available as a Snap, Flatpak or Appimage that will run without having to change shared libraries.
Cura and Slic3r, for example, (popular 3d printing slicers) are available as an Appimage, which needs no installation, as are Calibre, Gimp and many others

---

### Post by enricobe on 2018-08-16
> **wyliecoyoteuk said:**
> Each new application has to be tested against the main Distro's other packages, Kernel, etc. which is why bugfixes are added, but not new whole releases.
New releases may need new versions of libraries also used by other packages, and updating those may break other packages.Testing for this can be time consuming.
You must remember that many of the maintainers are volunteers who would rather be working on the next release.
If you want the newest versions of a package, see if it is available as a Snap, Flatpak or Appimage that will run without having to change shared libraries.
Cura and Slic3r, for example, (popular 3d printing slicers) are available as an Appimage, which needs no installation, as are Calibre, Gimp and many others

Thanks a lot for your explaination. Snaps on my Ubuntu are pretty slow to start and in this case I would prefer to use an older version of the program rather than the snap app :)

---

### Post by ajgreeny on 2018-08-16
Calibre is one of the very few applications that I install from a developer's own binary available at [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux).

However, I didn't find any real problems with the repository version before I became aware of the binary way; it was a recommendation from another respected forum user and calibre user who suggested I tried it.

Remember that once you move away from using standard repos you are, of course, on your own if you have any problems, so if version 3.21 works, don't fix it if you don't know how to solve your own problems.

---

