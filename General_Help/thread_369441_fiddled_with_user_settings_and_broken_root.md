---
title: "fiddled with user settings and broken root"
date: 2007-02-24
forum: General Help
---

### Post by Topace7 on 2007-02-24
i was fiddling with the user settings in xubuntu edgy and now and now cant seem to get anything done as root.

it is saying :

Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

when it would ordinarily ask for password.

it seems no user has root privileges anymore.

is it possible to sort this out somehow?
thanks.

---

### Post by nereid on 2007-02-24
You could boot your PC from the Xubuntu CD and chroot your root partition (assuming hda1 is your root partition)

```

booted your PC with Xubuntu CD
...
mkdir /mnt/root
mount /dev/hda1 /mnt/root
chroot /mnt/root /bin/bash

```

Now you're in your PC's harddisk. Just change the sudoers file (if this is the one where the error is) or add yourself to the admin group (if this is the reason for the error) or revert whatever you have done.

---

### Post by highneko on 2007-02-24
You might wanna look at your bash history. Maybe you'll notice something. 
```
gedit "$HISTFILE"
```

---

