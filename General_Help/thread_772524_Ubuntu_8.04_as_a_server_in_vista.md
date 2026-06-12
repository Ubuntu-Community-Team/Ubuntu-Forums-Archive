---
title: "Ubuntu 8.04 as a server in vista"
date: 2008-04-28
forum: General Help
---

### Post by ftpvk on 2008-04-28
I installed hardy heron as an application in vista. Just wanted to know, how can I load ubuntu within vista as an application. 

I do not want to boot into ubuntu from the beginning, because I want to use Ubuntu as a server, while doing casual stuff with vista.

Thanks for the help,

---

### Post by coolaj86 on 2008-04-28
You can, but not the way that it's supplied on the CD.

Do a quick google on VirtualBox, Qemu, coLinux, or cygwin.

VirtualBox is probably the easiest route. It's almost self explanatory once you download the app, but if you need any further direction post away.

Oh, and there is one little snag that you have to work through in Vista:
> 4.2.4 Windows Vista networking
Windows Vista no longer ships a driver for the AMD PCnet Ethernet card which is what
VirtualBox provides to the guest. As a result, after installation, Vista guests initially
have no networking. With Windows Vista guests, you will have to install a driver for
this card manually. For this reason, VirtualBox ships with such a driver, which, for
simplicity, we have added to the Guest Additions ISO.
To install this driver, mount the Guest Additions ISO (as described above, select
&#8220;Install guest additions&#8221; from the &#8220;Devices&#8221; menu). Then, start theWindows Hardware
Wizard and direct it to the Guest Additions CD where a driver for the PCnet card can
be found in the directory AMD_PCnet.

---

### Post by ftpvk on 2008-04-28
thanks, that worked

---

