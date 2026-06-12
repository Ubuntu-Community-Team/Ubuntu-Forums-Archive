---
title: "Trouble with Synaptic"
date: 2007-04-13
forum: General Help
---

### Post by Afkpuz on 2007-04-13
I'm getting a strange error everytime I try to install a package from synaptic.  After everything is downloaded and possibly installed (packages still seem to work despite this error), Synaptic tells me this:

The following problems were found on your system:
E: crystalcursors: subprocess post-installation script returned error exit status 2


The packages seem to work despite this message, but does anyone know how to put a stop to this?

-Thanks

---

### Post by laidback on 2007-04-13
I don't know the answer but you might like to try :-

Settings>Filters>Broken , select Broken in the lhs list click OK.

I'm not entirely sure how this works but I had a problem on a friends machine and by following this route synaptic then seemed to reinstall the offending programs and the error disappeared, presumably fixed.

---

### Post by Afkpuz on 2007-04-14
That didn't work

---

### Post by laidback on 2007-04-14
Sorry, hopefully worth the try.

---

### Post by x1a4 on 2007-04-14
Hi,

Most packages contain scripts which execute before and after installation.  The script  in your crystalcursors package returns with an error.  

Do you have KDE installed?  The crystal cursors are a KDE package, and if you don't have KDE installed, you don't have whatever API the script tries to access, thus it returns an error.

---

### Post by Afkpuz on 2007-04-16
Yea, that was the problem.  I'm not running KDE

---

