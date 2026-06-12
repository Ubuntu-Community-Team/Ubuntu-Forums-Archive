---
title: "openssh on a virtual machine?"
date: 2008-06-04
forum: General Help
---

### Post by Mets on 2008-06-04
I have an ubuntu virtual machine running via VirtualBox on a Windows XP host.  I'm trying to setup openssh so I can connect to Ubuntu and run programs both natively on windows and so I can access my files from outside of my home network.  I seem to be unable to connect to the VM with ssh, however.  I'm convinced that it is because right now they are running on the same IP address (somehow).  How would I change it so that they have their own IPs on the network?  Thanks!

Mets

---

### Post by geirha on 2008-06-04
It depends on how you've set up the network for your virtual machine. If you haven't set up the network, it is using the default, and with the default settings, you cannot contact your virtual machine, but the virtual machine can connect out.

So with the default setup, you only need to install an ssh-client to be able to connect to the ssh-server on your host-machine. I haven't tried openssh on windows, though I can imagine it's hard to set up. Try putty instead. Just a single executable. [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

