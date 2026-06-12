---
title: "Rox Desktop"
date: 2004-11-10
forum: General Help
---

### Post by seanf on 2004-11-10
Can anybody provide some guidance/instructions/experiences on getting ROX Desktop ([http://rox.sourceforge.net/](http://rox.sourceforge.net/)) installed on a Warty system?
 
I'm running Warty on an older laptop, and Gnome is decidedly un-snappy. XFCE4 runs somewhat faster, but the XFFM file manager is just weird enough to keep me looking for an alternative.
 
I know that the ROX site has instructions for installing ROX on Debian systems, just wondering if anybody had done it on Warty.
 
Thanks -
 
Sean F

---

### Post by az on 2004-11-10
Easy.  You can raid Debian.

Download this:
[http://archive.progeny.com/debian/pool/main/r/rox/rox-filer_2.0.1-3_i386.deb](http://archive.progeny.com/debian/pool/main/r/rox/rox-filer_2.0.1-3_i386.deb)


The info page is here:
[http://packages.debian.org/testing/x11/rox-filer](http://packages.debian.org/testing/x11/rox-filer)

sudo dpkg -i rox-filer*.deb

No menu entry, though.  Create one.  To start it run rox-filer.

I am a big fan of rox...

You can use a window manager like icewm (or even fluxbox...) and start rox with rox-filer -p=1) and you have a snappy desktop...

Beats the pants off xfce4!

---

### Post by seanf on 2004-11-10
Thanks for the tip!

I just noticed this though:

[http://archive.ubuntu.com/ubuntu/pool/universe/r/rox/](http://archive.ubuntu.com/ubuntu/pool/universe/r/rox/)

Unless I'm misinterpreting that, it seems that Rox is in Universe now.. although I updated my system a few days ago and did not see Rox in synaptic. Perhaps the update took universe out of my apt sources... not near the laptop now, will check it out tonight.

Thanks again!

Sean

---

### Post by az on 2004-11-10
I am pretty sure that the build daemons are working on Hoary.  You will have to use the Hoary universe archive to use that package.

Warty's Universe repository has been frozen since release.

---

