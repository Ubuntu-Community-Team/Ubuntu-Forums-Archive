---
title: "Installing Beryl on Edgy and loosing the X´s"
date: 2006-11-02
forum: General Help
---

### Post by el_nota on 2006-11-02
Hi! I followed this tutorial; [http://fredcpp.wordpress.com/2006/10/21/instalar-beryl-en-ubuntu-edgy-eft-con-nvidia-y-aiglx/](http://fredcpp.wordpress.com/2006/10/21/instalar-beryl-en-ubuntu-edgy-eft-con-nvidia-y-aiglx/) (it is in spanish) and after the 3-f) when I reboot I loose the X session and this error appear "cannot stat /etc/X11/X (no such file or directory), aborting" I tried to solve it by typing "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" but it does not work.
Any idea?
Thanks.

---

### Post by el_nota on 2006-11-02
Solved:

**sudo apt-get install xserver-xorg**
From recovery mode.

---

