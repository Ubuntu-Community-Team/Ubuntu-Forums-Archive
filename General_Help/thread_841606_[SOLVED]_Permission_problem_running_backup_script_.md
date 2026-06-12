---
title: "[SOLVED] Permission problem running backup script in Hardy"
date: 2008-06-26
forum: General Help
---

### Post by ashkev on 2008-06-26
I am trying to set up a computer for public internet access at a library.  In the past I have used a backup and restore script to maintain desktop settings etc.  I have created a user "guest" and the backup script is:

```
#!/bin/bash

IMAGES=/root/images
USER=guest

mkdir -p $IMAGES
rm -f "$IMAGES/$USER.tar"
tar -cpPf "$IMAGES/$USER.tar" "/home/$USER"
```

The restore script is:

```
#!/bin/bash

IMAGES=/root/images
USER=guest

mkdir -p $IMAGES
rm -fR "/home/$USER"
tar -xpPf "$IMAGES/$USER.tar"
```

These are in /root/.  When I try to run it:
```
guest@kevin-desktop:~$ cd /root
guest@kevin-desktop:/root$ sudo ./backup
[sudo] password for guest: 
Sorry, try again.
[sudo] password for guest: 
tar: /home/guest/.gvfs: Cannot stat: Permission denied
tar: Error exit delayed from previous errors
guest@kevin-desktop:/root$ 
```

Can anyone help?

Thanks

---

### Post by ashkev on 2008-06-26
Never mind.... I just needed to log out of guest, then everything worked.

---

