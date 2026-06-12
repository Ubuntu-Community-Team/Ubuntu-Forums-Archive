---
title: "Lock Ternimal - Prevent Terminal Close"
date: 2008-02-20
forum: General Help
---

### Post by neurostu on 2008-02-20
Hey this may sound like a silly question but is there anyway to "Lock" a window or prevent it from closing when Alt-F4 is pressed or when the X is clicked. 

I set up some SSH tunneling and use it throughout the day, but I also end up opening several terminals.  It is a bother to look at each window before I close them, it would be nice if I could close them all indiscriminately and have the "locked" window just stay open...

Any help is really appreciated.

---

### Post by seventhc on 2008-02-20
Not sure but you could put the one you want to remain open on a different workspace.

---

### Post by ahsile on 2008-02-20
I actually use the following for my tunnels at home. It is an alias in my .bashrc file:

alias sshtunnel='ssh -qTfnN -D 7070 my.tunnel.net'

The tunnel starts up, asks for my passphrase to unlock my private key, and then goes into the background never to be heard from again. Closing the terminal window isn't a problem after that!

---

