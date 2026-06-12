---
title: "how to delete guest option from login"
date: 2015-03-22
forum: General Help
---

### Post by tomsax on 2015-03-22
How do I delete the guest option from the account login or at least add a password.  I can't see this option in "accounts".

Tom

---

### Post by CantankRus on 2015-03-22
Check the directory** /usr/share/lightdm/lightdm.conf.d**
On my install the file to edit is **60-lightdm-gtk-greeter.conf**


```
sudoedit /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
```
or open the file however you like to open root text files.
and add the line...
```
allow-guest=false
```
May have to resart.

---

