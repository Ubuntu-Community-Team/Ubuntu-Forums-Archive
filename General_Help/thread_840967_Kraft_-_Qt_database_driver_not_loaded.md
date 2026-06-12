---
title: "Kraft - Qt database driver not loaded"
date: 2008-06-25
forum: General Help
---

### Post by firemane on 2008-06-25
I am trying to get Kraft to run on my Ubuntu box.

However, it keeps giving me this error: 

¨The Qt database driver could not be loaded. That probably means that they are not installed...¨

How/Where do I get the infamous Qt database driver?

---

### Post by bcnaat on 2008-11-22
In terminal:

```
sudo apt-get install libqt3-mt-mysql
```

Other than that I still can't seem to get it to connect to the database.

---

