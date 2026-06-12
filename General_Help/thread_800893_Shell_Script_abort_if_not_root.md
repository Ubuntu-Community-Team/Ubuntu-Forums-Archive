---
title: "Shell Script: abort if not root"
date: 2008-05-20
forum: General Help
---

### Post by oli_ on 2008-05-20
Hi,
is there a way to check within a shellscript if the script was called with root rights? ( sudo ./myscript )
if not it should print a warning and exit.
tried $USER, but it also shows my username if i sudo it (instead of root)

suggestions?

---

### Post by cdtech on 2008-05-20
You could use:

# Run as root
```

scriptname=`basename "$0"`

  if [[ $UID -ne 0 ]]; then
     echo "${scriptname} must be run as root"
     exit 1
  fi

```

Hope this helps.......

---

### Post by oli_ on 2008-05-20
nice, thats what i needed.

---

### Post by cdtech on 2008-05-20
welcome. :)

---

