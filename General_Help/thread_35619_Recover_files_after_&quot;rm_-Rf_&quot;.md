---
title: "Recover files after &quot;rm -Rf *&quot;"
date: 2005-05-19
forum: General Help
---

### Post by dovik on 2005-05-19
argh !  ](*,) 

unfortunately, i have done a "rm -Rf *" in my home (instead of my USB Key), and stop the execution with "Ctrl + C" ... but too late.

how can i recover my datas, my files ?

---

### Post by fng on 2005-05-19
Unless you have some professional disk-recovery-tools, your data is gone :(

---

### Post by Xian on 2005-05-19
For any tuning into this thread, please use the following command instead for safety if there is any doubt in what you are attempting to delete. It will prompt you to interactively delete the contents of occupied folders. 

```
$ rm -rfi <dir>
```

---

### Post by Sam on 2005-05-19
There is an app named "recover" (available in repo), but I didn't try it yet.

---

### Post by dovik on 2005-05-20
[QUOTE=Sam]There is an app named "recover" (available in repo), but I didn't try it yet.[/QUOTE]
i did.

it's working only for ext2.

i give up and i'm going to use an old backup.

thanks !

---

