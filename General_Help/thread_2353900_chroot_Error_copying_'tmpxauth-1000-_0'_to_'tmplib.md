---
title: "chroot: Error copying '/tmp/xauth-1000-_0' to '/tmp/libgksu-bCKUKv': No such file or"
date: 2017-02-26
forum: General Help
---

### Post by roberto32 on 2017-02-26
I'm trying to run firefox under chroot. So I did  ```
 gksudo chroot /chroot firefox -DISPLAY=:0.0but 
``` I get the error above Error copying ```
 '/tmp/xauth-1000-_0' to '/tmp/libgksu-bCKUKv': No such file or directory 
```
And when I'm in the chroot shell firefox -DISPLAY=:0.0 I get this error (firefox:16381):```
 Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.No protocol specifiedFailed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Error: cannot open display: :0.0
```What is wrong with it?

---

### Post by lisati on 2017-02-26
@roberto32: In future, please take the time to remove the AskUbuntu formatting before posting here.

---

### Post by roberto32 on 2017-02-27
ok I edited it a bit

---

