---
title: "FTPcube"
date: 2007-03-02
forum: General Help
---

### Post by nixfreak on 2007-03-02
Im using Ubuntu with Gnome on my server

I tried installing installing FTPcube i got an error saying i need wxpython,
itried installing wxpython then i got another error saying i need GLIB and GKT

GLIB installed fine but GTK giving this error:

```

checking pkg-config is at least version 0.9.0... yes checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.11.4 atk >= 1.9.0 pango >= 1.13.0 cairo >= 1.1.8) were not met. Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix. Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables to avoid the need to call pkg-config. See the pkg-config man page for more details.

```

Plz help.

Thanx in advance

Freak

---

### Post by tomski on 2007-03-02
are you trying to use 

'apt-get install'

if so try using 

aptitude install packagename

instead as this has better dependancy handling features and may help you even if it is a single .deb that you downloaded still try to install with aptitude because it will still try to search for the dependancies needed for that package

---

### Post by nixfreak on 2007-03-02
> **tomski said:**
> are you trying to use 

'apt-get install'

if so try using 

aptitude install packagename

instead as this has better dependancy handling features and may help you even if it is a single .deb that you downloaded still try to install with aptitude because it will still try to search for the dependancies needed for that package

10x for the reply....no i used ./configure before i got the error

i hope somthing is not wrong with tht system, coz i restarted my server now, and now it wouldnt log me in the GUI :S

im really new at linux so dont really know how t install all the appz, should i be using a normal account or should i use root? ive been doing from root till now, is tht the rite way?

---

