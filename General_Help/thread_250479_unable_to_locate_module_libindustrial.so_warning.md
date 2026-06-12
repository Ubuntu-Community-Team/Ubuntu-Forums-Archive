---
title: "unable to locate module libindustrial.so warning"
date: 2006-09-04
forum: General Help
---

### Post by yioan on 2006-09-04
Hello everyone,

When I load some applications using the command line (winetools, gcfclient(crossfire), pptpconfig) I get this message
"Gtk-WARNING **: Unable to locate loadable module in module_path: "libindustrial.so","

Does anyone what does it means? I checked for libindustrial.so and it exists in /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so. Should exist and somewhere else???

I get this message always with specfic applications. When I load evolution, for example, everything is fine.

---

### Post by kakyoism on 2006-10-29
i got the same problem, unfortunately...
somebody help...:(

---

### Post by dmc28 on 2006-11-22
Sounds like you're using an application that has a dependency on the older libindustrial.so, which explains why Evolution works fine.  Go to System -> Admin -> Synaptic, and search for gtk-engines-industrial(not gtk2*).  Mark that package for install and apply.  The warning should then disappear.

---

