---
title: "Unable to mount Network shares"
date: 2005-06-20
forum: General Help
---

### Post by Rounan on 2005-06-20
Sorry if this is considered a cross-post: a search returned [this thread](http://ubuntuforums.org/showthread.php?t=37323), and I replied there before realising it was the Warty forum. This is definitely a Hoary problem. Could an admin please relocate it if necessary?

Network shares won't mount on a fresh Hoary install. I get this error:

```

$sudo mount //host/share /mnt/point
mount: wrong fs type, bad option, bad superblock on //host/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg shows:
```
smb_fill_super: missing data argument
```

The machine is acting just fine as a samba server, and smbclient -L host works fine.

This appears to be a new or machine-specific issue, as I didn't run into it on another install a month ago. Is it possible that backports has broken something? This time around, I added the backport repositories before installing samba, and I'm running  version [3.0.14a-3ubuntu3~5.04ubp1].

Any help would be much appreciated.

--Rounan

---

### Post by xy77 on 2005-06-21
You could try:
```

$ sudo mount -t cifs //host/share /mount/point
# or
$ sudo mount -t cifs -o username=smbuser,password=smbpwd //host/share /mount/point

```

Note: cifs works for me, but maybe smbfs is worth a try.

Greetings
  David (xy77)

---

