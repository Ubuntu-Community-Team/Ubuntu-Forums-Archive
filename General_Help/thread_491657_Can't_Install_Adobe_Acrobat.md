---
title: "Can't Install Adobe Acrobat"
date: 2007-07-03
forum: General Help
---

### Post by wolfram32 on 2007-07-03
Hello,

I've run Adobe Acrobat Reader without problem on version 6.10.  I updated to version 7.04 and it wasn't installed anymore.  So I tried installing Acrobat with the tar.gz file on Adobe's website.  For some reason it didn't work.  

I then did a search and found out that I can install through the Synaptic Package Manager.  However, when I try to install through Synaptic, Synaptic spits out the following error and the installation stops:

[COLOR="Blue"]E: /var/cache/apt/archives/acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb: trying to overwrite `/usr/share/applications/AdobeReader.desktop', which is also in package adobereader-enu[/COLOR]

I've done searches and notice that others are having problems installing acroread on their machines, but I haven't seen anyone with the same problem I'm having. 

Does anyone have an idea how I can fix this?

Thanks.

---

### Post by kuja on 2007-07-05
It's a package conflict, Two different packages cannot try to install the same file, that just doesn't work. You'll have to remove either acroread or adobereader-enu.

---

### Post by wolfram32 on 2007-07-05
> **kuja said:**
> It's a package conflict, Two different packages cannot try to install the same file, that just doesn't work. You'll have to remove either acroread or adobereader-enu.

Thanks a lot for the tip.  I'm going to go through and scrub my drive of everything and try again.

---

### Post by wolfram32 on 2007-07-05
I did a search of my linux partition for every reference to adobe or acroread.  I then deleted them all, and tried to install from Synaptic.  It installed just fine.

Thanks again for your help, Kuja!!!:)

---

### Post by kuja on 2007-07-05
You're welcome.

---

