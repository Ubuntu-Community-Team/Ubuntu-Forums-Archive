---
title: "VMWare installation and xinetd"
date: 2007-09-24
forum: General Help
---

### Post by andreas.goransson on 2007-09-24
Hi!

I have installed the vmware-server package from feist-commercial today, worked like a charm! However, I had earlier installed vncserver in order to remotely manage the server. Then I installed vmware-server, xinetd got uninstalled. If I add vncserver again, vmware gets uninstalled due to xinetd installing again!

I am in desperate need of a solution so I can connect remotely to the machine and run VMWare server, anybody got an idea?

---

### Post by veloce on 2007-10-01
because I dislike vnc, I have a number of alternatives that I use.

1. to connect to a remote vmware-server I use vmware-server console

2. to remotely use a windoze machine (from linux or windows) I use rdp

3. from linux to linux I use XDMCP with Xephyr.

The only gap is windows to linux which I avoid.

Good luck

---

