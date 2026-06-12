---
title: "Improve locate search"
date: 2016-08-01
forum: General Help
---

### Post by 4kh3RAm on 2016-08-01
Is there a way to have locate find a file that only begins with say, uca instead of listing all files that have uca in the filename ?

```
#!/bin/bash
# 
#  Find files using a replaceable parameter
#
#     Searches ALL mounted drives
#
[ ! $1 ] && {
echo -e "Error!! No filename given. Searches ALL Drives and is Case Insensitive !!"; exit 1; } || echo -e "Searching for $1"
echo xxx | sudo updatedb
echo xxx | sudo -S locate -i $1

```

---

### Post by steeldriver on 2016-08-01
Does
```

locate '/uca'

```

do what you want?

---

### Post by 4kh3RAm on 2016-08-01
Thanks, worked great.

---

