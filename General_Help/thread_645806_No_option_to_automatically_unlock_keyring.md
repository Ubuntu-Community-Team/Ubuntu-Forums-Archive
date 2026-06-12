---
title: "No option to automatically unlock keyring"
date: 2007-12-20
forum: General Help
---

### Post by jordon on 2007-12-20
I upgraded from Feisty to Gutsy, but when I try to connect to my WiFi, I still have to enter a password to unlock the keyring every time. I think in Gutsy there's supposed to be an option to unlock the keyring automatically, but there's no checkbox - just a space to enter the password, like in Feisty.

I removed libpam-gnome-keyring (including configuration files) and reinstalled it, but I'm still having this problem. Can anyone please help?

---

### Post by linuxwizard on 2007-12-20
Look over this

[https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28keyring%29%7C%28password%29#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28keyring%29%7C%28password%29#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by jordon on 2007-12-20
I already did that. It worked in Feisty, but it doesn't work in Gutsy.

---

### Post by jordon on 2007-12-22
Can anyone help? This is really getting to me.

---

### Post by war59312 on 2008-01-02
Same here, does not work in Ubuntu 7.10. :(

> will@will-laptop:~/Desktop$  sudo apt-get install libpam-keyring
[sudo] password for will:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libpam-gnome-keyring instead of libpam-keyring
libpam-gnome-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by war59312 on 2008-01-12
One and only bump, anyone have a clue?

---

### Post by linuxwizard on 2008-01-12
Look through this, maybe a work around that will help.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247)

---

### Post by war59312 on 2008-01-12
Yeah I tried that and ended up getting locked out totally and having to do a recover boot and replace /etc/pam.d/gdm with /etc/pam.d/gdm~ .

ok that script working great now, turned out it was a preview entry in that file above and only caused the issue when autologin is disabled...

thanks a lot

---

