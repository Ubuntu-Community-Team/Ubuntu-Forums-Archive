---
title: "Configuring apache installation ..."
date: 2005-09-10
forum: General Help
---

### Post by dbee on 2005-09-10
Hi,

I want to install apache on my desktop server. I'm going to use it to serve files to the internet. I'm pretty particular about configurations though, and I'm more comfortable with the command line interface ... configure ... than with just letting apt-get take care of everything.

Basically I want to know how I can configure apache myself. If I use the command line to install the binaries, instead of aptget ... what functionality will I lose ? Is this bad for the system ?

How do I get to gain more control over the package install procedure which is so easy to use, but less familiar and possibly less secure than I would like ??? Again, this is going to be a working server, so I want to know exactly what goes into it ... and yes I do know that I could just look in apache.conf ... I'll also want to chroot the server.

---

### Post by amohanty on 2005-09-10
Heres what you can do to get the best of both worlds:

1. Install checkinstall from synaptic
2. Download apache source
3. ./configure --.....
4. make
5. sudo checkinstall 

This will create a .deb file and install it. To uninstall you can just do a
dpkg -r apache<whatever was before tar.gz>

HTH
AM

---

### Post by dbee on 2005-09-10
Excellent, thank you amohanty

---

### Post by theQmaster on 2006-01-24
I have apache2 installed using the synaptic if I'd uninstall it and get the sources and then compile them would I gain anything on performance ?

---

