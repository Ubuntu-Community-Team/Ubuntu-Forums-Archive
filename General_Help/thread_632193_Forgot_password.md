---
title: "Forgot password"
date: 2007-12-05
forum: General Help
---

### Post by bronzin on 2007-12-05
Hi to everyone!
I ve lost my username and password (they simply do not work!). I've watched many guides on internet about it (all these guides say: "Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username"   )

but it doesn't work!
There is a possibility that using Ubuntu with Wubi the steps are differents? Because in the grub menu I ve seen some differences between what I expected reading these guides and what I ve found (for example I ve to chose betwenn differents lines that starts with the word "kernel"...not just one...
I don t know if I was able to explain the situation but I hope so!

Thank u very much for your time!

Alfonso

---

### Post by scrooge_74 on 2007-12-05
I don't know but the theory says that when starting go into grub and choose safe mode

it will boot as root

since you already know your username type

passwd username
type new password
again

and that should be it reboot

---

### Post by ajgreeny on 2007-12-05
It's ```
passwd username
```note the double s or it won't work.  Otherwise the advice is OK.

---

### Post by ago on 2007-12-05
If you manage to install wubi (what version?) than it works as usual and the recipe you mentioned should be ok, if you are talking about a password problem during installation, then it might be a different issue.

---

### Post by jasper2076 on 2009-03-03
this helped me. thanks.

---

