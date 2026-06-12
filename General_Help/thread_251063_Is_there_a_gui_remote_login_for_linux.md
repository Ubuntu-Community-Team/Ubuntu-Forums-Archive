---
title: "Is there a gui remote login for linux?"
date: 2006-09-04
forum: General Help
---

### Post by jsmidt on 2006-09-04
For a windows machine using rdesktop, I can do a nice graphical login to a windows machine.  Is there a windows equivalant where I can login to my nice linuw desktop remotely.  I know ssh -X lets you open applications on an xserver, but is there a way to open my whole desktop?

---

### Post by zhenya on 2006-09-04
VNC is the traditional method, which allows graphical login across virtually every platform.  VNC is not secure on its own, so it will need to be secured over an SSH connection if you want to use it over the internet.  It also doesn't perform well without a relatively fast, low latency connection.  

While VNC certainly is still worthwhile, I'd recommend checking out FreeNX.  This allows secure, graphical logins with extremely tight compression that will send a full color desktop over a 56k (or slower!) connection!  For me, where VNC was often unusable over remote connections, FreeNX can provide an 'almost native' experience.  IMO it is also ultimately easier to configure than VNC over SSH.  Everything you need to know is in the archives!

---

### Post by hw-tph on 2006-09-05
X is network enabled by itself - that is how it was designed. Well before VNC even became an option you could run full remote desktops. Read the [XDMCP HOWTO](http://www.tldp.org/HOWTO/XDMCP-HOWTO/) for more information.


Håkan

---

