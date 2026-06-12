---
title: "Skype dont open ."
date: 2020-05-09
forum: General Help
---

### Post by Portaro on 2020-05-09
When I try to launch skype terminal return this :

```

skype
/snap/skype/123/bin/electron-launch: linha 31: /snap/skype/123/usr/lib/x86_64-linux-gnu/glib-2.0/gio-querymodules: Ficheiro ou directoria inexistente
/snap/skype/123/bin/electron-launch: linha 40: /snap/skype/123/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/gdk-pixbuf-query-loaders: Ficheiro ou directoria inexistente



```

I'm on Lubuntu 14.04. I install skype by snap.

---

### Post by Portaro on 2020-05-10
Solved , for some reason if you install the snap package he cant open, but if you optional download the .deb package of skype page and you install the package with terminal with [sudo dpkg -i] the deb install and then the two softwares are enable on the menu in my case I have two skype entries on menu and the software open well.

If you download the .deb package of skype and try to instal with gdebi he cant install because problems of dependencies that in my case are installed [libsecret].

Solved.

---

