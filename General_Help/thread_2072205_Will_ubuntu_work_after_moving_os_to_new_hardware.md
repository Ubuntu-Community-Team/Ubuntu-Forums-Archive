---
title: "Will ubuntu work after moving os to new hardware?"
date: 2012-10-17
forum: General Help
---

### Post by williammanda on 2012-10-17
I'm looking to upgrade the motherboard and cpu in an existing system with Ubuntu. Can I just simply change the hardware and Ubuntu will adjust ok or will I need to re-install Ubuntu?
Thanks

---

### Post by ubh on 2012-10-17
You can switch your HW without too much trouble.
The only things you should change are eth and wifi devices (the latter if it's installed on your mb) in```
/etc/udev/rules.d/70-persistent-net.rules
```. You'll also need to look at audio card configuration: _maybe_ it's to modify also that.

---

### Post by philinux on 2012-10-17
> **williammanda said:**
> I'm looking to upgrade the motherboard and cpu in an existing system with Ubuntu. Can I just simply change the hardware and Ubuntu will adjust ok or will I need to re-install Ubuntu?
Thanks

It should be fine I've swapped hard drives with ubuntu installed on different hardware no problem.

As always though backup any essential files etc.

---

### Post by kurt18947 on 2012-10-17
As ubh says, you shouldn't have a problem.  It'd be wise to uninstall any proprietary drivers -- video, networking etc.

---

### Post by PowerBarry43 on 2012-10-17
Hi 

Generally yes you'll normally have no problems although I've had trouble with grub not being detected if its not the first partition on the drive and the first one is reasonably big, that and as has been mentioned before proprietary drivers. Otherwise your good to go :)

Hope this helps!

Barry

---

### Post by Linuxisfast on 2012-10-17
Since all drivers are loaded with the kernel except those installed via hardware drivers which are usually proprietary, as long as you have removed those, it should boot.

---

### Post by williammanda on 2012-10-18
Thanks for all the replies! I removed the nvidia driver since an i7 was being installed. The change over worked without a hitch.

---

