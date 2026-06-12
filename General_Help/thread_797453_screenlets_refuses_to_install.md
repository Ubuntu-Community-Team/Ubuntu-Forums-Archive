---
title: "screenlets refuses to install"
date: 2008-05-17
forum: General Help
---

### Post by gegenki on 2008-05-17
EDIT:
I managed to install the next version down - which curiously didn't install earlier today but worked when I did it from command line using aptitude instead of apt-get


Once its marked for installation it says

screenlets:
```
 Depends: python-gnome2-desktop but it is not going to be installed
```

so naturally we move on to check that out.

Once I try marking that for installation - its the same but with another file
```
python-gnome2-desktop:
 Depends: libtotem-plparser10 but it is not going to be installed
```

```

libtotem-plparser10:
  Depends: libcamel1.2-11 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
  Depends: libedataserver1.2-9 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
```

both of which are installed along with their dev files

---

### Post by rune0077 on 2008-05-17
Try with the latest screenlets from [here]("http://www.getdeb.net/app/Screenlets")

---

