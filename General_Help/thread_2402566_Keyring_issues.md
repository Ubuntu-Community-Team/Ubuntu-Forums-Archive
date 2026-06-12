---
title: "Keyring issues?"
date: 2018-10-01
forum: General Help
---

### Post by zachalexy on 2018-10-01
Hi, never had issues but since a few days my keyring seems to be corrupted. Every logon I have to re-enter my login pwd. Can't save it with the remember checkbox. Everytime new Login entries are created:

[ATTACH=CONFIG]281229[/ATTACH]
Any help?, Thx, Zach!

---

### Post by again? on 2018-10-01
If you autologin the login keyring won't be unlocked.

From your pic it appears the Default keyring is being unlocked and not the Login keyring.

Is libpam-gnome-keyring still installed?
This is the module that automatically unlocks the Login keyring using your login password.
It is only a recommended dependency of gnome-keyring so may have been accidently removed.
```
apt policy libpam-gnome-keyring
sudo apt install --reinstall libpam-gnome-keyring
```

Do a test.
Move your ~/.local/share/keyrings folder to your Desktop as a backup.
```
mv ~/.local/share/keyrings ~/Desktop
```

Logout and back in.
The ~/.local/share/keyrings directory should have been recreated and seahorse
should show similar to pic with an unlocked Login keyring.
You may see a couple of chrome storage keys if you have opened a chrome browser. 
[ATTACH=CONFIG]281230[/ATTACH]

This wiki goes into a bit more detail about using the Default keyring as your store but
in my opinion it's easier just to start with a fresh ~/.local/share/keyrings directory where the Login keyring will be recreated.
[https://mxlinux.org/wiki/system/gnome-keyring](https://mxlinux.org/wiki/system/gnome-keyring)

---

### Post by zachalexy on 2018-10-02
Hi guber2, thanks! Reinstalling [COLOR=#000000][FONT=&quot]libpam-gnome-keyring and emptying [/FONT][/COLOR][COLOR=#000000]~/.local/share/keyrings did the trick. Great!!! Regards, Zach[/COLOR]

---

