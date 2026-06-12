---
title: "Ubuntu keeps asking me to unlock key chain every start up"
date: 2019-02-23
forum: General Help
---

### Post by dalekky on 2019-02-23
Just installed 18.04.2 LTS and chose to use auto-login at start up.

It logs in automatically fine, but then once at the desktop, I get prompted to enter the keychain password to unlock the keychain. 

This is completely impractical as this is on a PC used as a multimedia server connected to a TV and normally has no keyboard attached.

How do I find out what is causing the keychain prompt and how do I fix/remove it?

---

### Post by again? on 2019-02-24
Disable the keyring manager by setting a blank password on the login keyring.
[https://wiki.archlinux.org/index.php/GNOME/Keyring#Manage_using_GUI](https://wiki.archlinux.org/index.php/GNOME/Keyring#Manage_using_GUI)
*Note: "the old password" referred to should be your login password.

---

### Post by dalekky on 2019-02-25
that seems to have fixed it.

---

