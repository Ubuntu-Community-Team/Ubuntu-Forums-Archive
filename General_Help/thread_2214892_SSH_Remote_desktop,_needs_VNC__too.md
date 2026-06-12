---
title: "SSH Remote desktop, needs VNC/?  too?"
date: 2014-04-03
forum: General Help
---

### Post by BrianSwatton on 2014-04-03
I was under the impression that I could use SSH to operate desktops remotely, do I still need something like VNC as well to implement this?  

 I have now got an SSH server and client working. When I use "Remote Desktop Viewer" (Ubuntu Studio), I get a terminal rather than seeing the gui.

Thanks for reading

---

### Post by PartisanEntity on 2014-04-03
You have two options:

1. stick with the command line if you are comfortable with it.

2. Forward an X session over ssh: [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding) 

Have a look at the section titled Forwarding GUI Programs:

> If you are logging in from a Unix-like operating system, you can forward single applications over SSH very easily, because all Unix-like systems share a common graphics layer called X11. This even works under Mac OS X, although you will need to install and start the X11 server before using SSH. 

---

### Post by BrianSwatton on 2014-04-03
Thank you, reading now

---

