---
title: "Virtualbox does not recognize USB"
date: 2014-04-04
forum: General Help
---

### Post by 171742 on 2014-04-04
Hello,

I habe got ubuntu 12.4 32x. It only installs virtualbox 4.1.12 through the software center. Other versions do not compute. 

The problem is: The virtual machine does not recognize the usb (althogh ubuntu does). The extension pack of the newest version virtualbox 4.3 would help. but I cant install it.

Any solutions?

VMware player refuses to install altogether. Any solutions for this?

By the way, I need it for this:

[http://ubuntuforums.org/showthread.php?t=2214594](http://ubuntuforums.org/showthread.php?t=2214594)

Thanks!

---

### Post by kurt18947 on 2014-04-04
I've been using Virtualbox from the repositories.  I tried downloading and installing the guest extensions from the virtualbox site and had no luck.  Then I discovered guest extensions in the repositories and installed from there.  I now have video full screen but haven't tried USB connectivity.  This is on 14.04.

---

### Post by SeijiSensei on 2014-04-04
I suggest you remove any existing VirtualBox installations, then use the method described at the VB site for "[Debian-based Linux Distributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)."

After that is completed, download and install the [Extension Pack](https://www.virtualbox.org/wiki/Downloads) to add USB support (and other features).

---

