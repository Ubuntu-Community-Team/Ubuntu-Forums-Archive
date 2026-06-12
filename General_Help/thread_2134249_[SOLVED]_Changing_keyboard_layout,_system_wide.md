---
title: "[SOLVED] Changing keyboard layout, system wide"
date: 2013-04-10
forum: General Help
---

### Post by ofnuts on 2013-04-10
While installing my new Ubuntu (Kubuntu 12.10, but I don't think the 'K' is really important here) I made a misinformed choice of keyboard layout. I can change it in the KDE desktop, but this only applies to the desktop applications, and I would like the same layout in the TTY sessions. I changed the keyboard in /etc/default/keyboard but I still get the unwanted behavior in TTY sessions.

If that matters, I have a LUKS encrypted disk, so the keyboard layout is normally active before LUKS asks for the passphrase which is pretty much unavoidable with an AZERTY keyboard(*).

(*) before anyone warns me about the risk of not being able to type the passwords after the layout change, I just want to switch between two AZERTY variants, and I still have a AZERTY/QWERTY compatible passphrase anyway :)

---

### Post by ofnuts on 2013-04-15
Asnwering my own question:

```

sudo dpkg-reconfigure keyboard-configuration

```

Other setup from the installation can also be changed that way if you know the corresponding package name.

---

