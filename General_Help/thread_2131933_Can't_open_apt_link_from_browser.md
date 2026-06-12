---
title: "Can't open apt link from browser"
date: 2013-04-03
forum: General Help
---

### Post by Frozenic on 2013-04-03
need help here..yesterday I update my xfce from 4.8 to 4.10 (did it with xfce-dev ppa)..everythings is run normally but now Ican't open apt link (getdeb/ *playdeb) from my web browser..I think it because the new MIME type editor in xfce 4.10.. every I open an apt link it's open with xdg-open, but the xdg-open isn't open ubuntu software center that usually open automatically for apt link..how I fix this? I was trying to add it on ~/.local/share/ *application/ *mime blablabla, but its not working..

---

### Post by schragge on 2013-04-03
Check the output of
```
xdg-mime query default x-scheme-handler/apt
```

Also, have a look at [http://askubuntu.com/questions/tagged/apturl](http://askubuntu.com/questions/tagged/apturl)

---

### Post by Frozenic on 2013-04-03
The output is correct.. its open with ubuntu-software-center.desktopbut when I try to open an apt link (I try from terminal)for example```
xdg-open apt:wvdial
```I recieve an error dialog -unable to detect the URI-scheme of "apt:wvdial"-

---

### Post by schragge on 2013-04-03
I'm not sure about it, but try to install *apturl*

---

