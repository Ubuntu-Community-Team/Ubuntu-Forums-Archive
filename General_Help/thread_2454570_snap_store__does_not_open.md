---
title: "snap store  does not open"
date: 2020-12-02
forum: General Help
---

### Post by incedis on 2020-12-02
Have this box for a while now. 
Snap store does not open any more. 
I did install it, as is, a while back and it has always work out the box without me doing much.  Don't like command line very much. Computers are not my thing :) be kind please. 

I found the below error in logs

/snap/snap-store/498/usr/bin/snap-store: error while loading shared libraries: libgdk_pixbuf-2.0.so.0: cannot open shared object file: No such file or directory

Much appreciate some help..

I do run updates  as soon as they come out.. Probably something broke ? I don't have much install and never tinkered with the box as I don't like it very much. I believe the editor knows best.

I believe all the libraries are installed
&#10140;  ~ sudo dpkg-query -l | grep libgdk-pixbuf         
ii  libgdk-pixbuf2.0-0:amd64                   2.40.0+dfsg-5                       amd64        GDK Pixbuf library 
ii  libgdk-pixbuf2.0-bin                       2.40.0+dfsg-5                       amd64        GDK Pixbuf library (thumbnailer) 
ii  libgdk-pixbuf2.0-common                    2.40.0+dfsg-5                       all          GDK Pixbuf library - data files 
ii  libgdk-pixbuf2.0-dev:amd64                 2.40.0+dfsg-5                       amd64        GDK Pixbuf library (development files)

---

### Post by CelticWarrior on 2020-12-02
Please run
```
sudo apt update && sudo apt full-upgrade
```

Post here any errors.

---

### Post by incedis on 2020-12-02
Thanks 
All packages are up to date. 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
&#10140;  ~

---

### Post by tea for one on 2020-12-02
Open a terminal and try this:-
```
snap-store
```
Any error messages?

---

### Post by incedis on 2020-12-04
ah yes we got a winner.. thanks 
internal error, please report: running "snap-store" failed: cannot find installed snap "snap-store" at revision 481: missing file /snap/snap-store/481/meta/snap.yaml

What is the next step ?

Is it bad Doc ?

---

### Post by Dennis N on 2020-12-04
Refresh all snaps and see if that helps. My snap store (rev 481) is ok.
```
snap refresh
```

---

### Post by Dennis N on 2020-12-04
The file mentioned snap.yaml is present on my system in the location given. Strange that it should disappear. You could purge snap-store and install it again.

---

### Post by incedis on 2020-12-18
Just did a fresh install. It got too complicated for my little head :P

---

