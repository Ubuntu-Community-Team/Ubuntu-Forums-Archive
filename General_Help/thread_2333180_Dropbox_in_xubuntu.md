---
title: "Dropbox in xubuntu"
date: 2016-08-07
forum: General Help
---

### Post by donmatas on 2016-08-07
Hello,

I have installed dropbox through the terminal:

```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -

```

It is installed, but the icon is not visible. I tried with:

```
dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start

```

However, it does not work:

```
$ dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start
Dropbox isn't running!
Starting Dropbox...Dropbox isn't running!
Done!
matas@Autonomia-o-Barbarie:~$ 
(dropbox:7010): GLib-GObject-WARNING **: cannot register existing type 'GdkDisplayManager'

(dropbox:7010): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(dropbox:7010): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
```

Is there a solution?

thanks!

---

### Post by howefield on 2016-08-08
After the first command which downloaded and unpacked dropbox, did you run..

```
~/.dropbox-dist/dropboxd
```

In any event, much easier to install via the .deb file.

---

