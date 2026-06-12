---
title: "Install from source code sflphone"
date: 2014-01-13
forum: General Help
---

### Post by vpn9601 on 2014-01-13
You must install sflphone on Ubuntu 13.10. Link to the installation files [http://sflphone.org/download/stable-release](http://sflphone.org/download/stable-release). Tell me how to install.

---

### Post by 3rdalbum on 2014-01-13
Try clicking on the link in the Ubuntu PPA instructions (the link in the box, just after the word 'deb'). Click dist and then click 'raring'. Download the packages and then install them with a double-click.

See if it works - basically you would be trying the version for 13.04 on 13.10.

---

### Post by vpn9601 on 2014-01-13
W: Error  GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release:  The following signatures could not be verified because the public key is not available: NO_PUBKEY 9842E7BDE8E242F4

How to add a key?

---

### Post by Yellow Pasque on 2014-01-13
> **vpn9601 said:**
> How to add a key?

[http://sflphone.org/gnupg-key](http://sflphone.org/gnupg-key)

---

### Post by ajgreeny on 2014-01-13
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9842E7BDE8E242F4
```should do it for you, I think, though I am not certain of the **ubuntu.com** part of the command as it probably needs the address of the site you are trying to use; is this a ppa?

---

### Post by vpn9601 on 2014-01-13
Thank you! Install and operate!

---

