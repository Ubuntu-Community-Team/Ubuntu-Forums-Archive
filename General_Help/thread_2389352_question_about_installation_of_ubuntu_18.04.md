---
title: "question about installation of ubuntu 18.04"
date: 2018-04-15
forum: General Help
---

### Post by hunterkasy on 2018-04-15
I have noticed in the installation process of ubuntu 18.04 it doesn't ask about encrypting the home folder.  does it automatically do that as default or are they no longer having it as a option.

---

### Post by sudodus on 2018-04-16
They no longer have 'encrypted home' as an option in the installer. The home directory will *not* be encrypted. But there is still 'encrypted disk' as an option.

At the partitioning window of the installer select

[LIST]
[*]Erase disk and install Ubuntu
[*]Encrypt the new Ubuntu installation for security
[*]Use LVM with the new Ubuntu installation
[/LIST]

and in the next window select a very good security key. You will live with this key as long as you have this encrypted system. If you forget the key, your system will be lost. If the key is too simple or easy to guess, your system is not well protected.

[hr][/hr]
At the 'Who are you?' window, where you enter the user name and password, there used to be an option to select 'encrypted home', but it is no longer there. You can install the necessary program packages and create 'encrypted home' manually, but I recommend that you use 'encrypted disk' instead.

---

