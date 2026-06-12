---
title: "Connect to server from 2 PC"
date: 2013-09-13
forum: General Help
---

### Post by waffen on 2013-09-13
Hello,
I have this requirement: 2 ubuntu desktop machines need to connect to Ubuntu Server 13.04 like remote desktop, but both need to be independant, so each one can see the server desktop and run process, programms, etc but each one independant.

If I use shared desktop both see the same and do the same at the same time and thats not the idea. How can I make a solution for this? thanks in advance!

---

### Post by nerdtron on 2013-09-13
The server has a desktop interface?
What programs/process you need to run?

Why not create two accounts on the server. Then you both login using separate accounts (via ssh would be enough?). Then run your programs.

---

### Post by waffen on 2013-09-15
Yes the server have gnome-core installed, I can found a solution using NX Server and the Nomachines client, thanks!!

---

