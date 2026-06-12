---
title: "Problems with chgrp"
date: 2006-11-30
forum: General Help
---

### Post by ante on 2006-11-30
I'm having a problem with chgrp (or chown for that part).

I want to change the group ownership of a file but constantly get "Operation not permitted".

Example:
BBB@localhost$ ls -la myFile
-rw-rw-rw-   1 AAA BBB 2800 2006-11-26 15:07 myFile

BBB@localhost$ cat /etc/group | grep AAA
AAA:!:7000:BBB
BBB:!:7002:AAA

BBB@localhost$ chgrp AAA myFile
chgrp: changing group of 'myFile': Operation not permitted

(Please ignore spelling, this is but an example)

So, what to do? 

(I have my self used groupmod to change group membership...)

Thanks
A

---

### Post by taurus on 2006-11-30
Try to put a sudo in front of your command!!!

```
sudo chgrp AAA myFile
```

---

### Post by ante on 2006-12-01
Yeah, that will work, but I'm afraid I wasn't clear enough in my first post. 

The problem is that chgrp is executed in a script that must be run with user priviliges. I doesn't want to use the root account in this case...

Thnx


> **taurus said:**
> Try to put a sudo in front of your command!!!

```
sudo chgrp AAA myFile
```

---

