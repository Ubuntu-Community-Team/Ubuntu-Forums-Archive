---
title: "Trackpad"
date: 2021-01-20
forum: General Help
---

### Post by Philip_Edwards on 2021-01-20
Hi,
Acer Aspire V running Ubuntu 20.04

I've recently noticed that the trackpad no longer works.
I actually use a mouse but I'd like to use the trackpad.
Strangely the touchscreen works.

Any fixes available?

Phil

---

### Post by ActionParsnip on 2021-01-20
Try the boot option:
```

i8042.nopnp

```

May help

---

### Post by Philip_Edwards on 2021-01-20
Hi, What do I do with that piece of code.
It did nothing in Terminal.
Phil

---

### Post by ActionParsnip on 2021-01-20
Run:
```

sudoedit /etc/default/grub

```

change the line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nopnp"

```

Save the new file, close the editor and run:
```

sudo update-grub

```

Reboot to test

---

### Post by Philip_Edwards on 2021-01-21
Hi, I got stuck on "Save the new file".
I could make the changes but couldn't see how to save them.
Phil

---

### Post by howefield on 2021-01-21
Try Ctrl + O, then enter and finish with Ctrl + X

---

### Post by Philip_Edwards on 2021-01-21
Hi, Now I'm getting this. I think I might give up before I make a huge mistake.

E325: ATTENTION
Found a swap file by the name "/etc/default/.grub.swp"
          owned by: root   dated: Thu Jan 21 12:55:50 2021
         file name: /etc/default/grub
          modified: YES
         user name: root   host name: phil-Aspire-V5-573P
        process ID: 11947
While opening file "/etc/default/grub"
             dated: Thu Dec 03 09:30:04 2020


(1) Another program may be editing the same file.  If this is the case,
    be careful not to end up with two different instances of the same
    file when making changes.  Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/default/grub"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/default/.grub.swp"
    to avoid this message.
"/etc/default/grub" 33 lines, 1210 characters

---

