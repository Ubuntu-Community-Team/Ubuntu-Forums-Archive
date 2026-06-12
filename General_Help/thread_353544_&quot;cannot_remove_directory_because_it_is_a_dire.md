---
title: "&quot;cannot remove directory because it is a directory&quot;"
date: 2007-02-04
forum: General Help
---

### Post by battleroyalex on 2007-02-04
Im trying to delete a folder in linux but I cant do it through the browser because I dont have premission. So I tried to do it in terminal this is what I did:

```
jim@jim-laptop:/etc$ sudo rm -d vmware
rm: cannot remove `vmware': Is a directory
jim@jim-laptop:/etc$ 
```

---

### Post by taurus on 2007-02-04
```
sudo rmdir vmware
```
Assuming it's an empty directory.  Otherwise, use
```
sudo rm -rf vmware
```

---

### Post by ~LoKe on 2007-02-04
Yep.  You can recursively delete directories/files at the same time using rm -r, but if it's an empty directory, you'll need to use rmdir.

---

