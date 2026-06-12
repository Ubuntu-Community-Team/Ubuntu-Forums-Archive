---
title: "Why do I have multiple Processes?"
date: 2007-11-03
forum: General Help
---

### Post by mmilitia9 on 2007-11-03
I was looking at my processes.. and I seem to have... 

8 gnome-vfs-daemon
8 dbus-daemon

Is this normal?

---

### Post by HermanAB on 2007-11-03
Yes, it is normal.  It allows multiple things to happen at the same time and provides for a smooth running system.  Otherwise, you have to sit and wait for the system to print a document so you can open a spreadsheet for example - as with MS DOS.

---

### Post by 444 on 2007-11-03
```

$ dpkg-query -s libgnome-vfs0
 ...
 GNOME VFS is the GNOME virtual file system. It is the foundation of the
 Nautilus file manager. It provides a modular architecture and ships with
 several modules that implement support for file systems, http, ftp and others.
 It provides a URI-based API, a backend supporting asynchronous file
 operations, a MIME type manipulation library and other features.

``````

$ dpkg-query -s dbus
 ...
Description: simple interprocess messaging system
 D-Bus is a message bus, used for sending messages between
 applications.  Conceptually, it fits somewhere in between raw sockets
 and CORBA in terms of complexity.

```

So yeah, you need them. Lots of programs use dbus, to know if the internet connection is up for example.

---

