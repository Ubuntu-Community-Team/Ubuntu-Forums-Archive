---
title: "Clients booting into terminal server's root directory in LTSP5/Feisty?"
date: 2007-09-19
forum: General Help
---

### Post by RudeIota on 2007-09-19
I have a set up with diskless PXE clients and a Feisty server with LTSP 5. 

The question is: Should the server's root file system ALSO be the client's root file system? 

How did I notice this happening? The only way a client can login is enter an account name and password that is *local* on the server. I cannot login to accounts that have been chrooted in /opt/ltsp/$ARCH. 

I was under the impression that /opt/ltsp/$ARCH is supposed to be the 'root' directory for the client, not / ? Is using / instead of /opt/ltsp/$ARCH by design? Is this a bug or configuration error, perhaps? 

I'd be glad to offer more details for anyone that can shed some light on this.

---

### Post by RudeIota on 2007-09-19
For reference, this is by design. Here's the snippet:

> LTSP provides a terminal to get you logged into a server.

Once logged in, your session is running ON THE SERVER. It's no surprise
that if you start snooping around the filesystem, it looks just like the
servers filesystem. that's because IT IS the servers filesystem.

the stuff in /opt/ltsp/$ARCH is just what is needed by the thin client
to get booted up and launch an Xserver. From that point on, all
processing takes place on the server.

installing ubuntu-desktop or anything else in the chroot isn't gonna
magically make it run there.

We are working on the ability to run arbitrary applications on the thin
client, but that's a big issue, because we have to deal with things like:

a) How to get the app launched on the client, when you are logged into
the server.

b) How to make the users home directory available to the thin client
when it exists on the server

c) How to deal with multiple architectures. some apps should run
localy on some clients, but not all apps and not all clients.

I hope that helps,

Jim McQuillan

---

