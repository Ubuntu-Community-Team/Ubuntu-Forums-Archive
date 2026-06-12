---
title: "Installed to external HD, now want to change username"
date: 2008-02-29
forum: General Help
---

### Post by rfaith88 on 2008-02-29
I recently installed ubuntu on my external hard disk using information from this website: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Since I now have a persistent live cd, I would like to change the username from "ubuntu" to my name.  Unfortunately, when I went to the user and groups editor, it doesn't list it.  

Is there an alternate way to change this?

I was reading in a few bug reports that it may have to do with something called "casper" but I have no idea how to change this.

---

### Post by pointone on 2008-02-29
If casper is anything like live-initramfs (live-initramfs is a fork of casper) then the user is generated at boot with a script in /usr/share/casper/... And I'm not sure of the exact path after that. Perhaps /usr/share/casper/scripts/; look around for a script named "adduser".

---

