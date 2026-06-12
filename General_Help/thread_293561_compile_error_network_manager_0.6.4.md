---
title: "compile error network manager 0.6.4"
date: 2006-11-05
forum: General Help
---

### Post by ryu kun on 2006-11-05
I couldn't find any package for Network Manager's latest release 0.6.4 so I am trying to compile it myself (You can find the sources  [here]("http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/")). However I've got this error after ./configure command:

```
checking for wireless-tools >= 28pre9... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
```

I've checked in Synaptic that wireless-tools version 27+28pre13 is installed.

Any idea? What should I do now?

---

### Post by ryu kun on 2006-11-05
I've found it. **libiw-dev** is the needed package.

---

### Post by loko on 2006-12-18
i try to compile the version 0.6.4 of the network-manager and i get a problem.

make is aborting with this error:

```
../gnome/libnm_glib/.libs/libnm_glib.so: undefined reference to `dbus_connection_disconnect'
collect2: ld returned 1 exit status
make[3]: *** [libnm_glib_test] Fehler 1
```

but i think that i have all missing libs installed, can somebody help me?

---

### Post by marcantonio on 2006-12-26
Had the same issue.  Quick two line patch attached.  Or you can just replace:

```
dbus_connection_disconnect
```

with:

```
dbus_connection_close
```

in gnome/libnm_glib/libnm_glib.c

-Marc

---

### Post by loko on 2007-01-03
marcantonio,

thank you for this little patch, now everything compiles fine.

btw. can you tell me how you did find out, that it is now called 'dbus_connection_close' instead of   'dbus_connection_disconnect'?

---

### Post by amanita on 2007-01-30
Cheers man, your patch works! Thanks again  8-)

---

