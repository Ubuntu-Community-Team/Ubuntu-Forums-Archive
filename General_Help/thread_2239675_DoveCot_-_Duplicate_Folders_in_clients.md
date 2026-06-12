---
title: "DoveCot - Duplicate Folders in clients"
date: 2014-08-15
forum: General Help
---

### Post by CrimsonRider on 2014-08-15
A while back I've migrated a mail server from Courier-IMAP to DoveCot, mainly because of performance issues. The migration seemed to have worked, but, for some reason, all clients for all users display the entire folder structure twice.

I used the instruction on: [http://wiki2.dovecot.org/Migration/Courier](http://wiki2.dovecot.org/Migration/Courier) to migrate.
I use DoveCot 2.2.9 on 14.04

Clients used are either Thunderbird or RoundCube.

All folders seem to be duplicated on client side only. Anyone have an idea as to what is wrong?

---

### Post by SeijiSensei on 2014-08-15
Try moving $HOME/.thunderbird to .thunderbird.old, then launching the program.  It will rebuild its configuration.  Any better?

---

### Post by CrimsonRider on 2014-08-15
Alas, that didn't help. It also happens on multiple clients, Windows, Ubuntu 14.04 desktop, Mac, etc.

---

### Post by CrimsonRider on 2014-08-21
Anyone have any idea yet? This issue is quite annoying.

---

