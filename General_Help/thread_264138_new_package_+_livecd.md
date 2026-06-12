---
title: "new package + livecd"
date: 2006-09-24
forum: General Help
---

### Post by lopio on 2006-09-24
hi,
i'd like to propose ubuntu as linux preferite installation to my friends, win xp users.
I'd like to show them ububtu live and my question is about installing new packages in live cd from source files.
Running live cd distribution I saw it is possible to install build-essential amd compile new packages from source files.
In this way i compiled kismet.
I'd like to run this application on my friend laptop (with no internet connection) with ubuntu ubuntu livecd
On his laptop i can't download compiler end kismet source files cause internet is not available
Is it possible to save kismet produced binary for example on a usb storage to do this?

Another possibility is to save compiler binary and source files and recompile again recovering file via usb pen
Is it possibile to configure synaptic to do this?
thanks

---

### Post by tommcd on 2006-09-24
Well, you could download the build-essential as a .deb package from here:
[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)
Just right-click on it and install with 'GDebi package installer'. You could then download kismet and install it.
Welcome to ubuntu!! Hope this helps!

---

### Post by lopio on 2006-09-24
thanks for your help  -)
i don't undenstand how your suggest could be right with no internet connection cause i think this .deb files (very small) contains only info about packages not packages itself.
Excuse me for this newbie question...
EDIT: i think simple solution is to store deb files in my usb pen and then copy them in /var/cache/apt-get/archives of my friend laptop
thanks a lot

---

### Post by got_nix on 2006-09-24
if you feel  a bit idle you could even add the storage drive as a repo to your sources.list file and give your friend an example of apt-get show em how easy it can be to install applications that really sucker alot of win users into linux ;)

---

