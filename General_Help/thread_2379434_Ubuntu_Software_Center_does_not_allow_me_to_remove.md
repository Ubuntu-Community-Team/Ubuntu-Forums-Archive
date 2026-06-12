---
title: "Ubuntu Software Center does not allow me to remove app nor launch it"
date: 2017-12-05
forum: General Help
---

### Post by eraserpencil on 2017-12-05
Rambox on github that has 3 methods of installing it on Linux system via an AppImage, a supposedly .deb package, and detailed instructions for Linux installation. To the best of my ability, some worked, some didnt. I think I got a working copy after realising Ubuntu Software Center had them. 

I was doing some clean up of my system today and I removed the remnants of the above listed attempts and Rambox stopped working. It is not showing in dash, there is no Terminal executable. Ubuntu Software Center shows I have it installed, but clicking on the 'launch' button does nothing. Clicking on the 'remove' button creates 5 instances of Rambox under 'Installed' to be removed. I have deleted rambox folders in /etc, /bin, /usr/bin, ~/.config, did a ```
 grep -rni --exclude-dir={run,var,proc,sys,tmp,dev,lost+found,dir_*,media} rambox-0.5

```

I am not well versed enough yet to know where Ubuntu Software Center checks for installed packages, or where Dash checks to see what applications are installed. Would require advice on tracing the steps Dash takes to determine what has been installed, and the steps Ubuntu Software takes for Install, Remove and Launch interactions.

---

### Post by Kirk Schnable on 2017-12-05
See if there's still a trace of the package in the Dpkg database:

[B]dpkg --list | grep rambox

[/B]If there is, you might try removing it via apt:

**apt-get remove *nameofpackage***&#8203;

---

### Post by eraserpencil on 2017-12-06
> **Kirk Schnable said:**
> See if there's still a trace of the package in the Dpkg database:

[B]dpkg --list | grep rambox

[/B]If there is, you might try removing it via apt:

**apt-get remove *nameofpackage***&#8203;
 
It was the first thing I tried. 

When a .deb package is downloaded, Ubuntu Software opens with the corresponding package. I tried replicating that with rambox but it didnt work. Any ideas why?

---

