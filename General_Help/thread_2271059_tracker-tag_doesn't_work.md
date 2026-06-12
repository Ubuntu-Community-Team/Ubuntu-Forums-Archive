---
title: "tracker-tag doesn't work"
date: 2015-03-27
forum: General Help
---

### Post by tigerjack89 on 2015-03-27
I'm trying to use ```
tracker-tag
```.
However, whenever I try to add a tag to a file using ```
tracker-tag -a TAGNAME FILE
```, it returns 


 > Files do not exist or aren't indexed


Obviously, the file exists, but I'm not too sure of the "aren't indexed" part. Zeitgeist seems to be active. What could be the problem?

Thanks in advance

---

### Post by dino99 on 2015-03-27
have you set the full path of that tagname file ?

---

### Post by tigerjack89 on 2015-03-27
> **9d9 said:**
> have you set the full path of that tagname file ?
Already tried. Also, don't know if it can be useful, this is the output of

```
$>tracker-control
Found 294 PIDs&#8230;
Found process ID 3287 for 'tracker-store'
Found process ID 3300 for 'tracker-miner-fs'


Store:
27 mar 2015, 17:28:13:  &#10003;     Store                 - Idle 


Miners:
27 mar 2015, 17:28:13:  &#10003;     Applications          - Idle 
27 mar 2015, 17:28:13:  &#10003;     File System           - Idle 

```

---

### Post by tigerjack89 on 2015-04-11
up

---

