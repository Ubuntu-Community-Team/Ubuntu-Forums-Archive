---
title: "Installing outside apps"
date: 2005-05-01
forum: General Help
---

### Post by dragondash on 2005-05-01
I'm having trouble running ANY applications on Ubuntu that weren't included with the OS. I've tried running a few from burnt CD's, but none of the files are able to execute. Currently I'm trying with WINE, I have all the source code burnt to a CD, and I'm following the install instructions in the readme, but I can't seem to get it to work. Anyone have any suggestions? 

(just FYI, my linux box isn't connected to the internet, so any files I put on have to be downloaded on my Windows machine and burned to CD)

---

### Post by Juergen on 2005-05-02
A concrete error-message would help a lot.

But I suspect you didn't install the devel packages.
1) The c/c++-compiler isn't installed by default
2) All library packages are split into e.g.
   libfoo - to run apps that need this lib
   libfoo-dev - to **compile** apps that need this libs

You probably need several tries to get it all right. 
No way to network your boxes? That would make it much easier.

---

