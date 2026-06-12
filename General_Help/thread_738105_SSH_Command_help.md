---
title: "SSH Command help"
date: 2008-03-28
forum: General Help
---

### Post by matt12345678 on 2008-03-28
I am SSHed into a server. I am trying to copy a folder from my local disk to the server that I am SSHed into. I remember there was a way/command to do this but, I forgot. Is anyone familiar with SSH?

---

### Post by justleen on 2008-03-28
scp

from local to remote:
```

scp /local/file user@remotemachine:/path/to/destination/

```
from remote to local
```
 scp user@remotemachine:/file/to/copy/ /path/to/destination/ 
```

---

### Post by matt12345678 on 2008-03-28
I guess its only possible to do one file at a time? How about folders? Thanks the command really helps!

---

### Post by justleen on 2008-03-28
right, sorry

add a "-r" flag, for recursive.
that will get whole folders.

see man scp

---

### Post by anaconda on 2008-03-28
or use sshfs and fuse to mount the filesystem over ssh! That is cool. 

Then the remote folder would be just like a local folder, and you could copy to/from it normally with eg. nautilus..

---

### Post by matt12345678 on 2008-03-28
Thanks guys! Much appreciated!

---

### Post by justleen on 2008-03-28
sshfs doenst work with all SSH servers.... we got some (old, not openssh) ssh servers running, and i cant mount those..

but, yea, that works as well...

---

