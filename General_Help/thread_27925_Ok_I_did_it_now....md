---
title: "Ok I did it now..."
date: 2005-04-18
forum: General Help
---

### Post by ghettobanana on 2005-04-18
I was editing my /etc/sudoers file to remove firestarter and was talking to someone when i # the wrong line.   ](*,)  Now I can't sudo anything. 

I #'ed the %admin ALL=(ALL) ALL

I need to edit this file and of course I can't. 

# 1: (fail)
I edited my GRUB with init=/bin/bash
and once at the root prompt I nano /etc/sudoers
I was unable to save the file...says its read only.

Any advice?

---

### Post by ubuntu_demon on 2005-04-18
[QUOTE=ghettobanana]I was editing my /etc/sudoers file to remove firestarter and was talking to someone when i # the wrong line.   ](*,)  Now I can't sudo anything. 

I #'ed the %admin ALL=(ALL) ALL

I need to edit this file and of course I can't. 

# 1: (fail)
I edited my GRUB with init=/bin/bash
and once at the root prompt I nano /etc/sudoers
I was unable to save the file...says its read only.

Any advice?[/QUOTE]
 use this to gain root acces to edit your sudoers file :

[http://www.ubuntuforums.org/showthread.php?t=3609&](http://www.ubuntuforums.org/showthread.php?t=3609&)

edit : seems you tried that already .. maybe you should ask in that thread

---

### Post by az on 2005-04-18
rw init=/bin/bash


Did you forget the rw?

You can also just boot into recovery mode...

---

### Post by ghettobanana on 2005-04-18
damn I did forget the rw.

---

