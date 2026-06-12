---
title: "Virtualbox VboxVRDP issue"
date: 2007-04-17
forum: General Help
---

### Post by starfusionmz on 2007-04-17
I just installed a virtualbox and l like it much better than Vmware server but I having issue setting it up so that I can RDP to it. When I try and start the virtual machine with VboxVRDP 
I get
]Error message: VRDP server port 902 is already in use 
but I don't have anything else running that could be using that port
any ideas?

---

### Post by shoky on 2008-03-10
Port 902 is used by VMware for VMWare client connection.

Change VRDP port for Vbox to 3389 or something similar and then try

rdesktop -a 16 localhost:selected_port

This way You will connect to VBox RDP session.

---

