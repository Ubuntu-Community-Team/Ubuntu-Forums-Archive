---
title: "Shell script to test if a package has installed dependents?"
date: 2008-05-02
forum: General Help
---

### Post by sfp-a7x on 2008-05-02
Is there an efficient way to check if a particular installed package has any installed dependent packages?  The following works for me, but is REALLY slow for core packages (e.g., perl-base):
```
#!/bin/sh

if [ $(sudo apt-get -s remove "$1" | grep -c '^Remv ') -gt 1 ] ; then
    echo "Package $1 has installed dependents"
else
    echo "Package $2 does not have any installed dependents"
fi
```

Any suggestions?

---

### Post by olejorgen on 2008-05-02
```

if apt-cache rdepends $PACKAGE | xargs dpkg --status ; then
    echo $PACKAGE has installed dependents
else
    echo $PACKAGE does not have any installed dependents
fi

```

But it's probably not much faster, maybe slower. I guess rdepends is a expensive operation. EDIT: Or maybe it is.. apt-get remove probably figures out every package that needs to be removed

---

### Post by sfp-a7x on 2008-05-02
Thank you!  '[FONT="Courier New"]apt-cache --installed rdepends <package>[/FONT]' is just what I was looking for.

---

### Post by olejorgen on 2008-05-02
aha, I knew it should be a better way than that ugly xargs thingy

---

