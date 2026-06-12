---
title: "Shared Directory Permissions"
date: 2019-03-03
forum: General Help
---

### Post by poor-yorick on 2019-03-03
New-ish user, followed the example in Shotts's to set up a shared directory for two users. I would like to keep useful PDFs in this folder that both users can add files/directories to and read files from this directory.

My system only has two users ("joe" and "parity"). I created a new group ("library") with both of them in it.


```
joe@eta ~> cat /etc/group | grep library
library:x:1003:joe,parity
```

For some reason when I do `$ id` (logged in as "joe") I don't see the group listed, but when I do `$ id joe` I do see the group. I have logged out and logged back in after creating the group.

```
joe@eta ~> id parity
uid=1002(parity) gid=1002(parity) groups=1002(parity),27(sudo),1003(library)
joe@eta ~> id joe
uid=1000(joe) gid=1000(joe) groups=1000(joe),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),1003(library)
joe@eta ~> id
uid=1000(joe) gid=1000(joe) groups=1000(joe),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)
```

I have the same directory permissions as the Shotts book, but it won't let me write files/directories as "joe". 

```
joe@eta ~> ls -ld /usr/local/share/reference/
drwxrwsr-x 3 root library 4096 Mar  2 21:23 /usr/local/share/reference//
joe@eta ~> touch /usr/local/share/reference/testfile
touch: cannot touch '/usr/local/share/reference/testfile': Permission denied
joe@eta ~> mkdir /usr/local/share/reference/testdir
mkdir: cannot create directory ‘/usr/local/share/reference/testdir’: Permission denied
```

I am using 18.04 LTS. Can anyone explain what is wrong and how I can accomplish this shared directory?

---

### Post by TheFu on 2019-03-03
I think it should work, but if it isn't, try using '**newgrp library**', this will force library to be the effective group, not just another group in the list.
I don't have 18.04 and can't imagine why it wouldn't work if the session was really ended and restarted as a logout/login should do.

BTW, putting files like this under /usr/local/ might not be the best choice.  Check out the _file system hierarchy standards_ for what /usr/local/ is meant to be used and alternative locations. Google will find the wikipedia article.

---

### Post by poor-yorick on 2019-03-03
Thanks TheFu, `newgrp library` worked. I'll review the FS hierarchy standards. I thought that was an odd choice, but was simply intuition and Shotts sets up the shared directory in that location. Nothing is linked there yet so I'll put it somewhere more appropriate.

---

