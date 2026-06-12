---
title: "Remote Login via XDMCP ... advanced help"
date: 2007-11-23
forum: General Help
---

### Post by punzada on 2007-11-23
I've managed to get xdmcp running fine, but now I'm trying to kick it up a notch to a level I'm not even sure X server can do.

What I want to figure out is how to set it up so that a local user and remote user can log into the same X session and logout as they please?

Example:

Server
Laptop

User A on Laptop remote logs into Server via XDMCP
User B on Server, logs into the same user locally on the machine, and has the same X session as User A so that you can physically see what's being run graphically, and can manipulate it. If User B chooses they could also log out to their own user on Server and do their own thing, at any time wanting to return back to User A's account and viewing that same X session User A is on.

Forgive me, still learning the ins and outs myself, but is this even a possible situation? would it be insanely difficult to set up? Even if User A and User B couldn't share that x session at the same time it would be fine for me, as long as I could 'switch' the session depending on login (if that makes any sense at all)

any pointers for help in the right direction would be great, I know I could just remote desktop but that defeats the multi-user aspect I'm looking for.

---

### Post by punzada on 2007-11-25
bumping this to see if anyone else can give me any pointers or shoot me down as 'impossible' :P

---

