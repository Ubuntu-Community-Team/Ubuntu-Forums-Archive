---
title: "couldn't find package x-window-system-core"
date: 2008-04-01
forum: General Help
---

### Post by blairHarrett on 2008-04-01
Ok here is the story I have to do a project using Ubuntu server.
On this server I have to have installed
Apache Web Server
FTP Server
Samba Server
KDE Desktop

The first ones installed just fine and dandy. When I attempt to install x-windows-system-core I get this message "couldn't find package x-window-system-core" 

Ok now I am using the command "apt-get install x-window-system-core" while I am root. I have uncommented all the lines I in etc/apt/sources.list I don't know what is going on. Is a server down or something?

---

### Post by dcstar on 2008-04-01
> **blairHarrett said:**
> Ok here is the story I have to do a project using Ubuntu server.
On this server I have to have installed
Apache Web Server
FTP Server
Samba Server
KDE Desktop

The first ones installed just fine and dandy. When I attempt to install x-windows-system-core I get this message "couldn't find package x-window-system-core" 

Ok now I am using the command "apt-get install x-window-system-core" while I am root. I have uncommented all the lines I in etc/apt/sources.list I don't know what is going on. Is a server down or something?

Why are you trying to install that package?, it is a Debian component, not an Ubuntu one.

If you want the KDE desktop, then just install the **kubuntu-desktop** meta-package, that is what it is for.

---

### Post by blairHarrett on 2008-04-01
because I only want the KDE core I do not want kubuntu.

Bleh Unix was so much easier I hate GUI's on servers.

---

### Post by dcstar on 2008-04-01
> **blairHarrett said:**
> because I only want the KDE core I do not want kubuntu.

Bleh Unix was so much easier I hate GUI's on servers.

Then look at that meta-package and see what components you should be installing.

---

### Post by kerry_s on 2008-04-01
it's just " xorg " now.
so
sudo apt-get install xorg

will get you what you want. i guess ubuntu removed there's, here's what it say in debian.

```
transitional package for Debian etch 
This package is provided to smooth upgrades from Debian 3.1 ("sarge") to
Debian etch. It may be safely removed from your system. It depends on the
xorg package which is the new metapackage for installing the X Window
System in Debian.
```

---

