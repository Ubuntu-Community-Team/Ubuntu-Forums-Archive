---
title: "Can't restart or power off Desktop Hyper-V after logging in"
date: 2015-07-23
forum: General Help
---

### Post by brianbuchanan on 2015-07-23
I've installed Ubuntu 15.04 Desktop 64-bit in a Generation 1 Hyper-V VM in Windows 10 TPP Build 10162.  I'm not able to shutdown, or restart, after I've logged into the GUI; shutdown hangs at "Reached target Shutdown."

Shutting down from the first login screen works.  Shutting down from within a Guest session works.  I can't shutdown after logging into the GUI with my account, even if I logout first.  If I skip the GUI and login to vt1 I can shutdown.

All updates as of July 23, 2015 have been applied.  I've installed Thunar, Chrome and ownCloud client (from the OpenSUSE build service).  I've had to add GRUB_DISABLE_OS_PROBER=true to /etc/default/grub to get update-grub to work (this caused some installation and post-install update hiccups)  In /etc/default/grub I've also removed "quiet splash" from GRUB_CMDLINE_LINUX_DEFAULT so that I can see boot and shutdown messages, and when it hangs, this is what I see.

[IMG]http://i.imgur.com/SiQV4cA.png[/IMG]

Thanks for any help!

---

### Post by brianbuchanan on 2015-07-23
I turned off the VM's Dynamic Memory feature in the Hyper-V Manager and the problem has gone away.  Sorry for the trouble.

---

### Post by pianojeff on 2015-10-25
> **brianbuchanan said:**
> I turned off the VM's Dynamic Memory feature in the Hyper-V Manager and the problem has gone away.  Sorry for the trouble.
Thank you, **brianbuchanan**, for coming back and posting your solution. The same has worked for me! \\:D/

---

