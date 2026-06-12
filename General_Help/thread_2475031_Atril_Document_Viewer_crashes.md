---
title: "Atril Document Viewer crashes"
date: 2022-05-14
forum: General Help
---

### Post by donsy on 2022-05-14
It happens every time and with any pdf doc.

The following file appears in /var/crash:
```
whoopsie 1477315 May 14 07:13 _usr_lib_x86_64-linux-gnu_webkit2gtk-4.0_WebKitWebProcess.1000.crash
```

I searched the Internet but all I could find were bug reports. Does anyone know of a workaround?

Xubuntu 20.04.4 LTS
5.13.0-41-generic

---

### Post by Impavidus on 2022-05-14
No problem with atril on my Xubuntu 21.10 system. At least not with a pdf I created myself recently.

You could try a different pdf viewer, like evince or gv. evince and atril are both based on gtk3 and libpoppler, so they use the same underlying software. gv is independent, being based on ghostscript.

---

### Post by donsy on 2022-05-14
> **Impavidus said:**
> No problem with atril on my Xubuntu 21.10 system. At least not with a pdf I created myself recently.

You could try a different pdf viewer, like evince or gv. evince and atril are both based on gtk3 and libpoppler, so they use the same underlying software. gv is independent, being based on ghostscript.

Thanks, I like Atril so maybe I'll just wait and hope for an update. It was working fine not too long ago.

P.S. My daughter lives in Arnhem.

---

