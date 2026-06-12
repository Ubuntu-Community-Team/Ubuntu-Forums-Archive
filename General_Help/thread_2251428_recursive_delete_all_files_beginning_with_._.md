---
title: "recursive delete all files beginning with ._ ?"
date: 2014-11-04
forum: General Help
---

### Post by sohlinux on 2014-11-04
Hello, How can I recursive delete all files beginning with ._ ? thanks

---

### Post by steeldriver on 2014-11-04
To delete all such files from the current directory down,

```

find -type f -name '._*' -delete

```

or if you want to make it interactive (i.e. give you a chance to review each file and decide whether to delete it)

```

find -type f -name '._*' -exec rm -i {} \;

```

Note that these are true deletes - no second chances, no "restore from trash"

---

### Post by sohlinux on 2014-11-04
perfect. thanks

---

