---
title: "module-assistant to compile vmware-server modules"
date: 2008-03-18
forum: General Help
---

### Post by deepclutch on 2008-03-18
hi,
I have 2.6.22.386 kernel installed.the cannonical partner repo's vmware-server-modules packages misses the modules(vmmon and vmnet) for 2.6.22.386.
So,I thought of trying module-assistant before compiling a kernel(or module_image)
I have installed vmware-server-kernel-source . 
but a "m-a list"  doesnot shows vmware-source installed:confused:
So,what is the correct method to compile vmware-server modules with module-assistant.
Thank You!

**EDIT**:oh yes!I am having vmware-server & co installed from repository!not manual compiling :)

---

### Post by Dixie Flatline on 2008-04-06
Here's what I did, without using module-assistant.  I'm brand-new to both Debian and Ubuntu, so this may not be the Right way to do it, but it worked:

```
sudo apt-get install vmware-server-kernel-source
cd ~/src
tar xzvf /usr/src/vmware-server.tar.bz2
cd modules/vmware-server-kernel
sudo ./debian/rules binary-modules
dpkg -i /usr/src/vmware-server-kernel-modules-2.6.22.9-<my custom kernel id>_1.0.4-1gutsy2_amd64.deb
```

[INDENT]Note: there must be some better way to do this without sudo'ing when running debian/rules, but when I tried it with fakeroot instead of sudo, it failed because it wanted to create the .deb in /usr/src.  The "debian/rules binary-modules" command created /usr/src/vmware-server-kernel-modules-2.6.22.9-<my custom kernel id>_1.0.4-1gutsy2_amd64.deb[/INDENT]

I had compiled a custom kernel with HPET_EMULATE_RTC enabled to work around some timer issues with VMWare Server on my Dell SC440, and this did the trick.  After installing the .deb I created, VMWare Server starts without problems, and everything runs well.

Hope this helped.  As far as I can tell, module-assistant doesn't pick up on it because the package isn't named <something>-modules-source.

---

### Post by deepclutch on 2008-04-07
thanks for this!although I had used vmware installer to install and compile modules.
I have to update vmware with vmware-any-any-115(unofficial) though ;)

---

