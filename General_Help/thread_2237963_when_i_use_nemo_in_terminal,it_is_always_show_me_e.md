---
title: "when i use nemo in terminal,it is always show me errors."
date: 2014-08-05
forum: General Help
---

### Post by wulong710 on 2014-08-05
hello . when i use command nemo in terminal to open a folder, it is always occurse some warning.  
My laptop: acer4750g   ,  xcfe4. ubuntu14.04

command:
```
$ nemo ./
```

error log:
```
** (nemo:9577): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-BoYQfZ3g7B: Connection refused

(nemo:9577): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(nemo:9577): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```

---

### Post by vasa1 on 2014-08-05
But does Nemo work normally (other than the errors you see in the terminal)? Several programs throw up errors/warnings/messages which don't really affect their functioning. For more, look at [Why are there so many console messages from GTK+ applications?]("http://askubuntu.com/a/422400")

---

### Post by wulong710 on 2014-08-05
<rmzelnick> wulong710: try exporting NO_AT_BRIDGE
<rmzelnick> `export NO_AT_BRIDGE=1'
<rmzelnick> then try running nemo again

---

