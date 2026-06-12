---
title: "Removing Win4Lin."
date: 2007-05-21
forum: General Help
---

### Post by SirPaPa on 2007-05-21
Hello fellow Ubuntuers, I'm trying to remove Win4Lin from my system. I installed it yesterday but I didn't like it, specially after trying VirtualBox.

I removed a folder called "winpro" from my home directory(there's still a folder called "My Documents" related to Win4LinPro that I've yet to remove) but I want to remove the "win4linpro" from /opt to regain my disk space but don't know how.

So, I just tried to delete it but was denied permission.

Please, how do I go about completely removing Win4LinPro.

Thank you.

---

### Post by ghell on 2007-05-21
I have never tried win4lin or virtualbox (I use vmware-server if this is for the same purpose) so I have not experienced this myself.

Have you tried sudo rm -rf /opt/win4linpro

If you got it from the repositories (again, I don't even know if it is in them) you should be able to safely remove it all with apt-get remove.

---

### Post by SirPaPa on 2007-05-21
> **ghell said:**
> I have never tried win4lin or virtualbox (I use vmware-server if this is for the same purpose) so I have not experienced this myself.

Have you tried sudo rm -rf /opt/win4linpro

If you got it from the repositories (again, I don't even know if it is in them) you should be able to safely remove it all with apt-get remove.

Thank you for quick reply.

Yes, I've tried the command " rm -rf /opt/win4linpro" but it came back with " no such files or directory'.
 
Win4Lin is not in the repositories.
I got Win4lin at their site [http://www.win4lin.com](http://www.win4lin.com) ,but I stated previously I didn't like it. There's a .deb for it if you're interested.

---

### Post by ghell on 2007-05-21
Check the permissions on the files:

cd /opt/
ls -la

if you get a permission denied error you can usually just stick "sudo" in front on ubuntu and it will run the command as root. This is why i suggested sudo rm -rf rather than just rm -rf, in case you hadn't tried using sudo. It may have been giving an error if something in it was still in use, even if you had appropriate permissions.

---

### Post by SirPaPa on 2007-05-21
> **ghell said:**
> Check the permissions on the files:

cd /opt/
ls -la

if you get a permission denied error you can usually just stick "sudo" in front on ubuntu and it will run the command as root. This is why i suggested sudo rm -rf rather than just rm -rf, in case you hadn't tried using sudo. It may have been giving an error if something in it was still in use, even if you had appropriate permissions.

Thank you very much ghell, it worked. BTW did you check out Win4Lin?

Again, I thank you.:D

---

### Post by ghell on 2007-05-21
Nope, I'm very happy with vmware server for all my virtualisation needs :) It's probably the biggest, most popular piece of virtualisation software out there and "vmware server" is free. Many enterprises use other commercial versions of vmware like esx server.

I have not tried VirtualBox though a lot of people on this forum seem to like it (I have not really seen it even mentioned anywhere else) but if you want to give vmware-server a go, you can quickly install it as described here: [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by SirPaPa on 2007-05-21
> **ghell said:**
> Nope, I'm very happy with vmware server for all my virtualisation needs :) It's probably the biggest, most popular piece of virtualisation software out there and "vmware server" is free. Many enterprises use other commercial versions of vmware like esx server.

I have not tried VirtualBox though a lot of people on this forum seem to like it (I have not really seen it even mentioned anywhere else) but if you want to give vmware-server a go, you can quickly install it as described here: [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

I think I should also give VMWare a try. 

Thank you, now I'm curious.

---

