---
title: "forgotten SUDO password"
date: 2015-12-15
forum: General Help
---

### Post by sav3 on 2015-12-15
forgotten SUDO password
how do i reset

---

### Post by Tadaen_Sylvermane on 2015-12-15
if you can login to the system then the sudo password is the same as your user. if not then it's a matter of booting a live disk, chrooting into the installation and changing your user password and making sure /etc/sudoers matches what you need.

---

### Post by steeldriver on 2015-12-15
Provided you haven't set a password for the root account, there should be no need to chroot into the system - you can reset from a root shell in recovery mode

Just follow these instructions: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

