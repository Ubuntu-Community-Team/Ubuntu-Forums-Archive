---
title: "Localization (curency and decimal delimiters)"
date: 2008-05-03
forum: General Help
---

### Post by carl_s on 2008-05-03
Hello,
I'm trying to switch from Windows to Ubuntu but have a problem that I can't solve.

I can't find where to change the way currency (and other decimal numbers) are presented. In Windows it's possible to change this in one place and have the settings propagated to all applications, is there a similar function in Ubuntu?

Does anyone know how to do this or how I can help to provide a Swedish localization profile?

---

### Post by carl_s on 2008-05-03
I found a solution and thought that I might share it. This is what I did:

1) I checked what locales that where available on my system by looking in /usr/lib/locale (where I found the sv_SE.utf8 directory)

2) I edited /etc/environment and added the following lines:
LC_MONETARY="sv_SE.utf8" 
LC_NUMERIC="sv_SE.utf8" 
LC_TIME="sv_SE.utf8" 
LC_PAPER="sv_SE.utf8" 
LC_MEASUREMENT="sv_SE.utf8" 
LC_TELEPHONE="sv_SE.utf8" 
LC_ADDRESS="sv_SE.utf8" 
LC_NAME="sv_SE.utf8" 
LC_COLLATE="sv_SE.utf8" 
LC_CTYPE="sv_SE.utf8"

3) I rebooted the computer and verified that the changes worked by running the command locale

---

