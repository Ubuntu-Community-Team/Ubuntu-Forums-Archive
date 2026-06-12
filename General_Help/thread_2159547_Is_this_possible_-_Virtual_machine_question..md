---
title: "Is this possible - Virtual machine question."
date: 2013-07-03
forum: General Help
---

### Post by zozza on 2013-07-03
Hello, 

I use Ubuntu 12.04. I access Windows XP from a Oracle VM VirtualBox. I set up the Guest Additions so that the VM can access selected folders on the Ubuntu hard drive.

However, I wonder if it is also possible to access the VM (when XP is running) from within Ubuntu? Can I create files from within the VM and access them from Ubuntu?  Or is this not possible?

I am not experienced with VMs so please explain in simply language if possible!  Many thanks!

---

### Post by varunendra on 2013-07-03
> **zozza said:**
> However, I wonder if it is also possible to access the VM (when XP is running) from within Ubuntu? Can I create files from within the VM and access them from Ubuntu?  Or is this not possible?

Directly accessing the guest drives is not possible. However, you can "share" the drives within the guest (XP) and access them from within Ubuntu just as you would access any shared folder on the network. In this case, the host (Ubuntu) will see the guest (XP) as a different machine located on the local network, and will access its shares via network.

In VMware, you can enable directly copy-paste of objects (not only text) between guest and host, but even that is not a "direct access" of drives/folders.

If accessing files created within the guest (xp) is all you need, it is already supported in the shared folder you currently have. Just make sure the share is not marked as 'Read-Only' in VM's settings. Map this shared folder as a network drive in XP, then use it a local drive to create or read files in it.

---

