---
title: "Can not install Personas in LibreOffice 4.x"
date: 2013-04-28
forum: General Help
---

### Post by NBPX on 2013-04-28
[COLOR=#000000][FONT=verdana]

I'm trying to make LibreOffice less ugly. On the configuration screen of the Personas I put the link to the page of the Persona, but nothing happens.
[/FONT][/COLOR]

---

### Post by Dennis N on 2013-04-28
Mozilla has changed the URL for the personas from [www.getpersonas.com/...](www.getpersonas.com/...) to [https://addons.mozilla.org/...](https://addons.mozilla.org/...). 

Unfortunately, Libreoffice expects a URL beginning with [www.getpersonas.com/](www.getpersonas.com/) and will not accept anything else until this problem is fixed by a future update. The term personas also seems to have been tossed aside - now they are themes.

If you installed them before this change, they still work, because Libreoffice stores a local copy of the persona graphics. Mine have survived through at least one LO update through the PPA.

---

### Post by NBPX on 2013-04-29
It's possible to download and install a Persona manually?

---

### Post by Frogs Hair on 2013-04-29
You can locate your installed personas .  [http://askubuntu.com/questions/270962/download-save-persona-files](http://askubuntu.com/questions/270962/download-save-persona-files)

---

### Post by Dennis N on 2013-05-02
Update: Persona problem now fixed in upgrade to L.O. version 4.03~rc2 from PPA. Tried it, it works.

---

