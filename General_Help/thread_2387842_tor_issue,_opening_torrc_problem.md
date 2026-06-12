---
title: "tor issue, opening torrc problem"
date: 2018-03-24
forum: General Help
---

### Post by hunterkasy on 2018-03-24
I have always used this: sudo gedit /etc/tor/torrc  to open my torrc file for editing,
now when I try I get this:

```
tyler@tyler-ssdnew:~$ sudo gedit /etc/tor/torrc
[sudo] password for tyler: 
No protocol specified
Unable to init server: Could not connect: Connection refused
```

```
(gedit:2364): Gtk-WARNING **: cannot open display: :0
tyler@tyler-ssdnew:~$
```

---

### Post by Frogs Hair on 2018-03-25
What release ? Opening graphical application using sudo is not recommended because it can cause permission problems in the file system. Safe alternatives include sudo -H gedit or gksudo gedit if gksu is installed.

---

