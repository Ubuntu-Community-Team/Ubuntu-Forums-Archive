---
title: "libdb.so.3 needed for VMware Management Interface (web)"
date: 2006-10-18
forum: General Help
---

### Post by OMEGA_ReD on 2006-10-18
Does any one knows where i can get the libdb.so.3 needed for the installation of VMware Management Interface?

I can't find it in the add/remove application.

thanks!

---

### Post by OMEGA_ReD on 2006-10-20
Anyone a suggestion?

---

### Post by OMEGA_ReD on 2006-10-21
No one? realy need your help here :P

---

### Post by psifertex on 2007-03-28
Don't know what the "right" way to fix it is, but here's what worked for me:

```
sudo apt-get install libssl0.9.7 libdb1-compat
sudo ln -s /lib/libdb.so.2 /lib/libdb.so.3
sudo ln -s /usr/lib/libssl.so.0.9.7 /usr/lib/libssl.so.4
sudo ln -s /usr/lib/libcrypto.so.0.9.7 /usr/lib/libcrypto.so.4
sudo ln -sf /bin/bash /bin/sh
```
That seemed to clear it up for me, but ymmv.

---

