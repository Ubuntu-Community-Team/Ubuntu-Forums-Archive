---
title: "Nautilus network:/// times out"
date: 2012-11-04
forum: General Help
---

### Post by lordzanny on 2012-11-04
I have a fresh install of 12.10 with stock everything, and attempting to browse network or go to network:/// or smb:/// in Nautilus errors out with a timeout.  It won't recognize shares on the host or any other machine on the lan.

A half hour of googling didn't turn up anyone else with a similar issue.  Networking is working fine, ssh works, vnc works (as well as vnc on Unity does.. yay for no screen refresh bug).

Any ideas why the network would always time out?  I have another Ubuntu machine running 12.04 on the same network and it works fine.  Browsing the local network also works from the liveusb on the same machine.

---

### Post by Tasu on 2012-11-05
Hi, I solved by installing cifs-utils and winbind:

sudo apt-get install cifs-utils winbind

---

