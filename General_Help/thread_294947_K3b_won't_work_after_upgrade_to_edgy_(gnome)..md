---
title: "K3b won't work after upgrade to edgy (gnome)."
date: 2006-11-07
forum: General Help
---

### Post by CheeseEatingBulldog on 2006-11-07
I love k3b as it burns pretty much every type of iso file you can imagine, but since I have updated to edgy I can't get it to work. I have reinstalled k3b, the libs, kde, kde-desktop and can't get it to open, so I tried it in a terminal to see the error and got this:

bulldog@ifrit:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/bulldog/.kde/socket-ifrit/kdeinit__0'
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.

Any ideas?

---

