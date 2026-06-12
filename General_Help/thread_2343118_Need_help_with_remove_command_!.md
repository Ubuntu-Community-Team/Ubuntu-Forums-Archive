---
title: "Need help with remove command ?!"
date: 2016-11-13
forum: General Help
---

### Post by fairbird on 2016-11-13
I use this option to delete all png photo from this directory 
/enigma2/python/Plugins/Extensions/OpenWebif/public/images/remotes
Just I want to keep some png photo (dm800.jpg, dmm1.png, dmm2.png, dm_normal.png, w_remote.png)
But after trying all the png have been deleted
 any advice please ?!
Thank you 
```

do_install_append() {
    for l in `find "${D}/${libdir}/enigma2/python/Plugins/Extensions/OpenWebif/public/images/remotes" | egrep '\.png$'`
        do
          case "$l" in
          ("dm800.jpg"|"dmm1.png"|"dmm2.png"|"dm_normal.png"|"w_remote.png") echo keep $l;; 
          *) rm -rf $l;; 
          esac
        done
}

```

---

### Post by steeldriver on 2016-11-13
What do you want advice on, specifically? Why the command didn't work as expected (hint: the `find` results include paths)? How to test commands like `rm` before running them for real? How to recover the files?

---

### Post by fairbird on 2016-11-13
Solved by this link
[http://stackoverflow.com/questions/22558245/exclude-list-of-files-from-find](http://stackoverflow.com/questions/22558245/exclude-list-of-files-from-find)

I do this
```
do_install_append() {
for i in `find /"${D}${PLUGINPATH}/public/images/boxes" \( -name "*.jpg" ! -name dm800.jpg ! -name dm500hd.jpg ! -name dm800se.jpg ! -name dm8000.jpg ! -name dm7020hd.jpg \)`
        do
             rm "$i" 
        done
}
```

---

