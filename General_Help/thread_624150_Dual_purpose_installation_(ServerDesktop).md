---
title: "Dual purpose installation (Server/Desktop)"
date: 2007-11-26
forum: General Help
---

### Post by tofagerl on 2007-11-26
I have a (whitebox) computer I will be running as a server, mostly for VMware and some development work (Tomcat, apache and so forth).
However, at times I will have to use a normal desktop with Gnome, Firefox, OpenOffice.org, the VMware server console and other things.

I know I could simply dualboot the server distro and the desktop distro, but that means I will have to power down all my VMs every time I need to check something on Wikipedia, which is not ideal.

My thinking is that I want to be able to install the server distro with VMware, and then have the Desktop packages installed but inactive, unless I start the services I need with a /etc/init.d/ script. Then after I am done, I want to be able to unload them. I want to do this with a single init.d script that calls the other scripts from within. However, I don't know which services I need to load to get a desktop.

Can anyone point me in the right direction?

---

### Post by PeterJS on 2007-11-26
You are so close, in fact that script is already written for you. Install from the server disk, then install the ubuntu-desktop meta package, and lastly use update-rc.d to stop gdm from running on boot. Then to start the desktop stuff run sudo /etc/init.d/gdm start, and jump over to vt7, and then stop it when you're done.

---

