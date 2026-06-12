---
title: "NoMachine NX Free session problem"
date: 2012-10-25
forum: General Help
---

### Post by nanoVapor on 2012-10-25
Hi,

I'm first in linux world and it's the first time using Ubuntu. All the problems that I've found I could solve looking the solutions over the web, but I stuck here:

I have Ubuntu 12.10 installed on my machine with NX Free Client, Node and Server with 2 users: administrator user and a test user.
I also have installed Gnome-shell with the fallback session extension.

On my work machine (Windows 7), I have NX Free Client for Windows installed. I configured the node.conf to intiate the gnome session with the fallback.

If I try to connect using the administratior credentials, I can only see the desktop and the icons on it.

If I try to connect using the test user, everything goes right. To acess my admin account, I have to load the NX Client inside the test session to access my administrator account. Doing this, I can get everything working right.

Any ideas how can I solve this?

Sorry my bad english.

---

### Post by nanoVapor on 2012-10-26
Any one? Sorry if this is the wrong area...

---

### Post by QIII on 2012-10-26
Do you have both connections configured to be interactive?

Do you have a separate server.cfg on the server for each user?  Are the values for enabling interactive session shadowing and desktop sharing the same.

---

### Post by nanoVapor on 2012-10-26
Hi, thanks for the reply.

I dont't think that I'm using separete server.cfg for each user.. How can I check it?

I'm using the default configuration of NX Free.. The interative session shadowing and desktop sharing values are the same...

---

### Post by nanoVapor on 2012-11-01
I'm just about to create another administrator user in order to make this happen.. But I'm wondering why my default administrator user fail on show the Gnome-classic and the test user works fine showing it...

---

