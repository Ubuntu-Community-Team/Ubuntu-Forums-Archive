---
title: "[SOLVED] rsync script debugging - help!"
date: 2007-11-30
forum: General Help
---

### Post by njparton on 2007-11-30
Can someone please help me debug an rsync script before I add it to cron:

```

#!/bin/sh

rsync Fred:password1@vistapc smb://vistapc/WindowsMail /media/Backup  

```

I have something similar working via cygwin in Windows but I don't particularly like that solution as I regularly re-install Windows.  I run my ubunutu box as a nas so doing it this way would seem like much less hassle in the long run.

I can see the windows drive via smb (smb://vistapc/WindowsMail) and read files from it successfully. The user Fred exists on both machines with the same password.

I get the following error when I try to run the above:

```
rsync error: syntax or usage error (code 1) at main.c(1151) [receiver=2.6.9]
```

can anyone help me here?

Thanks

---

### Post by njparton on 2007-12-01
Surely someone can help?

---

