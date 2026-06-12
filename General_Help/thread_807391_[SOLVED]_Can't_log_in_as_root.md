---
title: "[SOLVED] Can't log in as root"
date: 2008-05-25
forum: General Help
---

### Post by RobHK on 2008-05-25
I accidentally locked my root password by pasting sudo passwd -l root into a terminal.

Now I can't log in as root. How can I reverse this? I get a message that the administrator is not authorised to log in.

---

### Post by ibuclaw on 2008-05-25
```
sudo passwd -u root
```
The above command, with a bit of luck, should unlock the account.

Regards
Iain

---

### Post by aysiu on 2008-05-25
You don't need to log in as root. Try ```
sudo -i
```

---

### Post by Prospero2006 on 2008-05-25
I think you can pass the grub bootloader something along these lines

```

init=/bin/bash

```

That might let you in.

---

### Post by RobHK on 2008-05-28
> **Prospero2006 said:**
> I think you can pass the grub bootloader something along these lines

```

init=/bin/bash

```

That might let you in.


I had a particular reason to want to log in as root; the VirtulBox setup was refusing to let me do some things without it. But in the end I decided toscrap the installation because I couldn't get the proper screen size.

I did crack the root password though, with: sudo passwd -u root

---

