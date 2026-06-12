---
title: "installing new fonts"
date: 2007-04-24
forum: General Help
---

### Post by cptjaben on 2007-04-24
I've just gotten some new fonts and I'm wondering how to install them in ubuntu. I know in windows you simply add them to a folder, i believe c:/windows/fonts or something of the sort. How do i do something like this, but in Ubuntu? Thanks

---

### Post by amohanty on 2007-04-24
If they are not installed by deafult the recommended location is:
/usr/local/share/fonts

also once you put them there, dont forget to do a 
sudo fc-cache -f -v

or log out and log back in.

HTH
AM

---

### Post by cptjaben on 2007-04-24
Worked perfectly, thanks for the help.

---

### Post by centyx on 2007-04-25
I tried this also, but without success.

fc-cache reports "/usr/local/share/fonts/vgafonts: caching, 0 fonts, 0 dirs"

I am trying using the fonts from [http://home.earthlink.net/~us5zahns/enl/ansifont.html](http://home.earthlink.net/~us5zahns/enl/ansifont.html), which I have used in the past on earlier versions of Ubuntu. Then, I ran update-fonts-dir manually. That does not appear to work now. 

Any suggestions?

Thanks!

---

### Post by deanlinkous on 2007-04-26
open file manager
use the address bar - type in fonts:///
hit enter
drag/drop the files in

(works in debian etch)

---

