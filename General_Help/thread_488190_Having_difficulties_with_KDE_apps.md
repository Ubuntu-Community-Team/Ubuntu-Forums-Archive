---
title: "Having difficulties with KDE apps"
date: 2007-06-29
forum: General Help
---

### Post by Mr Greencastle on 2007-06-29
I'm having some trouble trying to run KDE apps in Ubuntu Feisty
I just recently formatted my system and started fresh, but it seems that any KDE app that I try to start just plain won't!
Am I missing some libraries or something?
I'll post the output of Ktorrent when I run from a terminal...
```
mrgreen@Mars:~$ ktorrent
trying to create local folder /home/mrgreen/.kde/share: Permission denied
trying to create local folder /home/mrgreen/.kde/share: Permission denied
trying to create local folder /home/mrgreen/.kde/share: Permission denied
trying to create local folder /home/mrgreen/.kde/socket-Mars: Permission denied
trying to create local folder /home/mrgreen/.kde/socket-Mars: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/mrgreen/.kde/socket-Mars/kdeinit_localhost_1'
ERROR: KUniqueApplication: Can't setup DCOP communication.
mrgreen@Mars:~$ 

```

It works when I run it under sudo, but then it won't let me load any of my torrents...
This is the same for K3B, Konversation and any other KDE app I try.

Thanks for all the help!

Mr Green

---

### Post by Mr Greencastle on 2007-06-29
Bump,
I really appreciate all help!

---

### Post by bettlebrox on 2007-06-30
The files were probably created with  ownership by root when you ran ktorrent using sudo. 

What does the following command show?

[INDENT]ls -ld /home/mrgreen/.kde/share[/INDENT]

---

### Post by Mr Greencastle on 2007-06-30
It gives me a permission denied. How would I give myself permission to run these programs?

---

### Post by McNils on 2007-06-30
```
sudo chown -R mrgreen:mrgreen /home/mgreen/.kde
```

---

### Post by Mr Greencastle on 2007-06-30
Yep, thanks, that worked!

I'll remember that 'chown' command :D

Mr Green

---

