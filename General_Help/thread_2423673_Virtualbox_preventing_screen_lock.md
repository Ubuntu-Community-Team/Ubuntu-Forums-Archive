---
title: "Virtualbox preventing screen lock"
date: 2019-07-27
forum: General Help
---

### Post by joburg on 2019-07-27
Ubuntu 16.04 LTS

     I have gone back to Ubuntu 16.04 after I have tried and rejected 18.04. But even with 16.04 I have now a problem. I have noticed that if I have a Virtualbox virtual machine open, my screen does not lock anymore as it did with 14.04. This is a serious security risk for me as all my data remains available through the virtual machine. Is there any way that I can get the screen to lock while a virtual machine is open?

---

### Post by TheFu on 2019-07-27
Which screen saver do you use?

I don't use virtualbox, but it works fine with xscreensaver, kvm+libvirt VMs.  The xscreensaver settings are controlled by either the .resource file or through the xscreensaver-demo tool.

---

