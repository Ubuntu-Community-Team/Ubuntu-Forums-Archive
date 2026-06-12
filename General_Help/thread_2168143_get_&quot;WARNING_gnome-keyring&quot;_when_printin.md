---
title: "get &quot;WARNING: gnome-keyring::&quot; when printing"
date: 2013-08-16
forum: General Help
---

### Post by sam_baker2 on 2013-08-16
When I print out to my large size printer, I get this in the terminal ( but the printer prints out ok )
```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-YnBi9L/pkcs11: No such file or directory
```

I have a /tmp/keyring, but is is not the number shown in the message ( YnBi9L ), and also, there
is no "/pkcs11" in the keyring folder.

My large size printer is set as the deafult printer and I use this command to print ( for example a file called "plotfile")
and I have the printer connected through a USB connection:

```
lpr plotfile
```

I use 12.04 xubuntu

Thanks

---

### Post by DavidBiesack on 2013-10-09
I have a similar problem, but a different path. I'm running xubuntu 13.04 , lightdm, and x4ce session (not gdm)
when I try to lpt I get an error

$ lpr git-cheat-sheet-v2.pdf 
WARNING: gnome-keyring:: couldn't connect to: /run/user/<userid>/keyring-OpztsQ/pkcs11: No such file or directory

I do have gnome-keying running.

---

