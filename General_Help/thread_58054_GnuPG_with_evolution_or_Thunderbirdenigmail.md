---
title: "GnuPG with evolution or Thunderbird/enigmail"
date: 2005-08-18
forum: General Help
---

### Post by Blase on 2005-08-18
I all !

I originally posted this in the PPC thread (as I run Ubuntu on a powerbook) 
but thought this is a best place.

Here the first post:
[http://ubuntuforums.org/showthread.php?p=305612#post305612](http://ubuntuforums.org/showthread.php?p=305612#post305612)

I'm trying to use GnuPG with either evolution and
enigmail in thunderbird, but no one of both are working . . .

GnuPG seem to work fine in terminal, as I generate a key,
-- list-key show me the key correctly.

evolution error message:

```
Impossible to create the message,
cause "gpg: skipped '0x330BB...' : secret key not available.
gpg: signing failed: secret key not available
```

Enigmail error message:
```
Send operation aborted

Error -encryption command failed

gpg command line and output:
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --clearsign --digest-algo sha1
-u <info@.......> --passphrase-fd 0 --no-use-agent

gpg: skipped <info@.......> : secret key not available
gpg: [stdin]: clearsign failed: secret key not available
```


What I'm doing wrong ?

Thanks in advance !

---

### Post by Blase on 2005-08-20
Still don't want to work . . .  

Any help, please  :grin:

---

