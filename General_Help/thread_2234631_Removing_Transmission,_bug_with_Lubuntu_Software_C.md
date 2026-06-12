---
title: "Removing Transmission, bug with Lubuntu Software Center"
date: 2014-07-15
forum: General Help
---

### Post by linux_dream on 2014-07-15
Lubuntu 14.04 comes with Transmission. I wanted to uninstall it, so I used the Lubuntu Software Center, and uninstalled it from there. However this automatically installed Qtransmission. So I removed it, still from the Lubuntu Software Center. However this automatically installed Transmission. Removing Tranmission once more still automatically installs Qtransmission, etc. It's an infinite loop.  I am sure I am not the only one with this problem. Here's a fix:  Open the terminal and type: ```
sudo apt-get remove --purge transmission transmission-common transmission-gtk 
```. Once done, ```
sudo apt-get autoremove
```. This procedure works for me.  I would report this bug to the Lubuntu community if I knew how to do it properly...

---

### Post by vasa1 on 2014-07-16
> **linux_dream said:**
>  ... I would report this bug to the Lubuntu community if I knew how to do it properly...
If you wish, you can sign up here: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

---

