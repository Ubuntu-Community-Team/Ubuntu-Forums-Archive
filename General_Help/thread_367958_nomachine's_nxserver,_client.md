---
title: "nomachine's nxserver, client"
date: 2007-02-22
forum: General Help
---

### Post by sefs on 2007-02-22
Hi all my nx set has started to give problems.  The error msg i get now when trying to log in remotely are....

[I]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/I]

I have also attached a pic of the error i get.

This was after recent updates for ubuntu

---

### Post by sefs on 2007-02-25
The culprit seems to be upnp on the adsl modem.  When enabled nxclient works, when disabled it does not.

---

