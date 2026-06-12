---
title: "About ubuntu-6.06-server-amd64"
date: 2006-08-08
forum: General Help
---

### Post by satimis on 2006-08-08
Hi folks,

About ubuntu-6.06-server-amd64

Is its base OS similar to Ubuntu-6.06-alternate-amd64 with packages for running server added?  OR there are some specific packages for server included on this OS?  TIA.

I have an Ubuntu-6.06-alternate-amd64 box.  Can I make it as ubuntu-6.06-server-amd64 server by adding appropriate packages on it?

B.R.
satimis

---

### Post by KaeseEs on 2006-08-08
The 'server' release has no X.org, nor any programs that require X, such as desktops and graphical programs.  It also uses a kernel patched for server use, rather than one patched for optimal desktop use.  

If you wish run servers off your desktop, your best bet is to install appropriate packages.  For example, to run a webserver, ```
sudo aptitude install apache2
``` Or, to run an ftp server, ```
sudo aptitude install proftpd
```

---

### Post by satimis on 2006-08-08
Hi KaeseEs,

Tks for your advice.

Are all operations run by command lines?

Is LVM supported?

TIA

B.R.
satimis

---

### Post by KaeseEs on 2006-08-08
Yep, everything is done by command line.  LVM is supported just the same as in the desktop version.  Oftentimes, server installs are run headless and administrated remotely, though that's of course not mandatory.

---

