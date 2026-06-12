---
title: "Error loFirst, try booting into recovery mode (dgging in to GDM, user not authorised"
date: 2006-11-03
forum: General Help
---

### Post by WhizCas on 2006-11-03
Hi,

Got a very strange problem and don't know how it started. When logging in im getting this error:

> GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.I do got disk space :-k

Then going in to ctrl+alt+f1, stopping gdm with commando: sudo /etc/init.d/gdm/ stop . After that im trying to startx: after that im getting this error:

> xauth: creating new authority file /home/cas/.serverauth.3751

X: user not authorized to rum the X server, aborting.
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
Couldnt get a file descriptor referring to the console

Help is really appreciated because im getting pretty desperated...

---

