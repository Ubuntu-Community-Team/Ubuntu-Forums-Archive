---
title: "display-dhammapada doesn't work"
date: 2007-05-13
forum: General Help
---

### Post by bpont on 2007-05-13
When invoking 'display-dhammapada' at the command line, I get the following error message:

```
/build/buildd/display-dhammapada-0.23/debian/display-dhammapada/usr/share/doc/display-dhammapada/dhammapada-english-transl.txt:/build/buildd/display-dhammapada-0.23/debian/display-dhammapada/usr/share/display-dhammapada/dhammapada-english-transl.txt:dhammapada-english-transl.txt
dp:     -- cannot open any of the files.
```

Any ideas how to fix this?

---

### Post by bpont on 2007-05-14
```
cd /

sudo mkdir -p /build/buildd/display-dhammapada-0.23/debian/display-dhammapada/

cd /usr/share/display-dhammapada

sudo ln -s /build/buildd/display-dhammapada-0.23/debian/display-dhammapada/

```

---

