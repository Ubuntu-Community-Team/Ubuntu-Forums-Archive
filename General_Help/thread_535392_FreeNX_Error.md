---
title: "FreeNX Error"
date: 2007-08-26
forum: General Help
---

### Post by lwranger3 on 2007-08-26
I have installed FreeNX on my Ubuntu server and the NX Client on a Windows Vista machine, both on the local network. Unfortunately when I try to connect it stops with the error "Session startup failed.". Clicking on Details reveals the following:

[COLOR="Blue"]...
NX> 105 /usr/lib/nx/nxserver: line 891:  5912 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.[/COLOR]

I have switched to an earlier version of the NX Client (1.5), which produces an unknown error before hanging on the initialization window with the words "Setting up the X environment".

I have checked the firewall and imported the key from the server into the NX Client but still no success.

Any ideas?

---

