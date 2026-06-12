---
title: "No GUI login for me"
date: 2014-01-17
forum: General Help
---

### Post by zrzhu11 on 2014-01-17
If I start ubuntu regularly, I couldn't see the login window for me. so I couldn't log in. however, if I am able to log in with previous linux version 3.5.0-44-generic by press "shift" key when I boot the computer. How can I fix it? Thanks.

---

### Post by kajoky on 2014-01-18
Do you have more than one operating system installed or is Ubuntu the only operating system you boot into? This sounds like a problem with GRUB.

---

### Post by jeanjd63 on 2014-01-18
Hello
I think it's a problème with the last kernel.
You can try an update :
[B]sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]

---

### Post by zrzhu11 on 2014-01-19
> **jeanjd63 said:**
> Hello
I think it's a problème with the last kernel.
You can try an update :
[B]sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]
No luck with the command.

---

### Post by zrzhu11 on 2014-01-19
> **kajoky said:**
> Do you have more than one operating system installed or is Ubuntu the only operating system you boot into? This sounds like a problem with GRUB.
I installed ubuntu within windows 8 by using Wubi. If that caused the problem, how can i uninstall the current kernel and use the previous one?

---

### Post by fosterD on 2014-01-20
May be you can try to reinstall lightdm, which manages the login screen.

Press Ctrl-Alt-F1 and login with your username and password
then
```
sudo apt-get install --reinstall lightdm
sudo dpkg-reconfigure lightdm
sudo reboot
```
Hope this could help

---

### Post by deadflowr on 2014-01-20
> **zrzhu11 said:**
> I installed ubuntu within windows 8 by using Wubi. If that caused the problem, how can i uninstall the current kernel and use the previous one?

Yeah, that's most likely the problem.
Says this at the top of the page [here]("http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows")
> [h=4][SIZE=2]Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.10.[/SIZE][/h]

And that would mean any version of wubi and windows8.

---

### Post by zrzhu11 on 2014-01-24
> **fosterD said:**
> May be you can try to reinstall lightdm, which manages the login screen.

Press Ctrl-Alt-F1 and login with your username and password
then
```
sudo apt-get install --reinstall lightdm
sudo dpkg-reconfigure lightdm
sudo reboot
```
Hope this could help
It worked. Thanks.

---

