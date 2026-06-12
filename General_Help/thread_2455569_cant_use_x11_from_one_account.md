---
title: "cant use x11 from one account"
date: 2020-12-22
forum: General Help
---

### Post by NotQuiteSU on 2020-12-22
I have an app which requires a GUI, so I'm using X11.

I SSH into AccountA, and am able to use x11 apps, no problem. I SU over to AccountB, which doesn't permit direct SSH.
When I try to launch the same app, I get the following:

> /usr/local/bin$ PuTTY X11 proxy: Unsupported authorisation protocol

(<app>:3254): Gtk-WARNING **: 15:18:06.685: cannot open display: <servername>:11.0


---

### Post by spjackson on 2020-12-24
This ought to do it:
```

AccountA$ chmod go=r ~/.Xauthority # Allow AccountB to copy this file
AccountA$ su AccountB
AccountB$ cp ~AccountA/.Xauthority ~

```

---

