---
title: "SSH permissions"
date: 2008-05-03
forum: General Help
---

### Post by StOoZ on 2008-05-03
Usually when I log into my computer using ssh, I type my user name an root password (im the only user on that machine).

I would like to create another user name + password,to use for logins via ssh, but, it would like it to have a restricted access to only one directory, I dont want it to be able to browse the computer/copy delete etc, unless it is in its our dir.

is it possible?

---

### Post by Monicker on 2008-05-03
Do a google search on the terms "ssh chroot jail".  It can be done, but its a bit of a pain. This functionality is not something native to the standard implementation of ssh.

---

### Post by StOoZ on 2008-05-03
thanks.

to make things clearer, ssh must be logged with root password?

---

