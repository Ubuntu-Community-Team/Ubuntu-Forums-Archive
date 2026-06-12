---
title: "Komoda by Active State"
date: 2005-05-21
forum: General Help
---

### Post by blindpete on 2005-05-21
Hello I'm very new to linux.  I have used Komodo by activestate for years on windows.  they have a linux version but I admit the sys requirements do not mean much to me.  I have they latest Ubuntu Hoary.

> Linux

    * Red Hat 7.3: Linux 2.2.0 Kernel, glibc 2.1+ and libjpeg.so.62+
    * Red Hat 8.x, 9.x, Red Hat Enterprise 3.0 and Fedora C2: Linux 2.2.0 Kernel, glibc 2.1+, libjpeg.so.62+
          o Note: Red Hat Linux 9.0 is known to have threading library bugs in older versions of its glibc that may cause Komodo to hang in certain situations. The recommended solution is to upgrade to the latest glibc for Red Hat Linux 9.0.
    * SuSe 8.2+: Linux 2.2.0 Kernel, glibc 2.1+, libjpeg.so.62+
    * SuSe 9.x: Linux 2.2.0 Kernel, glibc 2.1+, libjpeg.so.62+

[http://www.activestate.com/Products/Komodo/system_requirements.plex](http://www.activestate.com/Products/Komodo/system_requirements.plex)

Is it compatable?

---

### Post by GTvulse on 2005-05-21
[quote=blindpete]
Is it compatible?
[/quote]
In principle, yes. But there is another hurdle you need to jump. Judging by the Linux distributions they mention and you quote, the binary packages are in RPM format. You need to install or convert to deb format first and install second with the help of alien ("man alien").

---

