---
title: "Create directory with timestamp"
date: 2007-03-19
forum: General Help
---

### Post by pan69 on 2007-03-19
Hi guys,

I would like to create a directory with the current timestamp in its name from a shell script. Does anyone knows how to do this?

Thanks!

---

### Post by llamakc on 2007-03-19
```

#!/bin/sh
date="[FONT=verdana][SIZE=2][COLOR=#000000]`**date** +%Y%m%d`"
[/COLOR][/SIZE][/FONT][FONT=verdana][SIZE=2][COLOR=#000000]mkdir ${**date**}-mynameofdir
#or mkdir mynameofdir-${date}

```

```

ken@llamakc 07:12:49:~/bin$ ./datecircreate.sh 
ken@llamakc 07:12:51:~/bin$ ls
[COLOR=Navy]20070319-mynameofdir [/COLOR]

```The above script will create the directory in the directory it is run in.
[/COLOR][/SIZE][/FONT]

---

### Post by pan69 on 2007-03-19
Thanks mate!

---

