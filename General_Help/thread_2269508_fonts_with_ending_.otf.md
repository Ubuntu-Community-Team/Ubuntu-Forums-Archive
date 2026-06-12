---
title: "fonts with ending .otf"
date: 2015-03-16
forum: General Help
---

### Post by Pedroski55 on 2015-03-16
I downloaded some Chinese fonts. They have the ending .otf

I have found the easiest way to get fonts on my computer is download the font, copy it into /usr/share/fonts/anyfolder then

sudo fc-cache -rv

However, the fonts with the ending .otf are not picked up by this, and are not available in Libre Office.

Any tips please?

---

### Post by Bucky Ball on 2015-03-16
If you do a search for '.otf file ubuntu' you'll find lots of info about how to install them. Good luck and let us know if you get stuck. ;)

---

### Post by Pedroski55 on 2015-03-16
Ah well. I followed your advice. I read up. Afterwards, I made a directory called opentype in /usr/share/fonts/

There are 7 fonts ending .otf in there.

I ran sudo fc-cache -frv , which sees, among many others the directory opentype and installs 7 fonts.

/usr/share/fonts/opentype: caching, new cache contents: 7 fonts, 0 dirs


Fontviewer also says these fonts are installed. In Libre Office they are not available. I tried a reboot, but they are still not available.

Found the problem: for some reason the had the permissions rw r none 
All other fonts have rw ro ro , so I changed that to rw ro ro now they show up!

---

### Post by Bucky Ball on 2015-03-16
Excellent news and well done. Please mark thread as solved to help future travelers (see second link in my signature). Good luck. ;)

---

