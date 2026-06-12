---
title: "Add desktop to Server"
date: 2014-01-19
forum: General Help
---

### Post by held7over on 2014-01-19
Ubuntu 13.04 Server

I want to install the LXDE desktop as a light weight desktop on a very old machine that is too slow to run a regular desktop, but I don't want LXDE to launch automatically on boot. I want to be able to call it and dismiss it on the commandline. 

How do I do that???

Thanks for your thoughts and suggestions! :)

---

### Post by steeldriver on 2014-01-19
iirc if you install lxde-core (or even lxde without including the 'recommended' packages i.e. adding the --no-install-recommends switch to apt-get) it doesn't even include a display manager - so your only option is to start it manually - usually using the startlxde wrapper

---

