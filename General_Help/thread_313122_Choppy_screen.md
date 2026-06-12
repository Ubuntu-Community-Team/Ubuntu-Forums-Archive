---
title: "Choppy screen"
date: 2006-12-05
forum: General Help
---

### Post by fhslacrosse13 on 2006-12-05
I have a problem with the screen getting choppy when I scroll webpages are move different windows around.  I used easyubuntu to install the ati drivers for my card but I'm not sure is they are working.  Seeing as it is still choppy after installing them with easyubuntu I guess they didnt but Im not sure what to do to fix this.

---

### Post by Shatrat on 2006-12-05
The quick way to check is by typing ```
glxinfo | grep rendering
``` in a terminal.
If it says Direct Rendering: Yes then you are in business, however it sounds like you are in fact not in business.

Depending on what kind of card you have, you might want to use one of the more hands-on methods for installing the drivers (they are well described in how-tos in the multimedia forum).

---

