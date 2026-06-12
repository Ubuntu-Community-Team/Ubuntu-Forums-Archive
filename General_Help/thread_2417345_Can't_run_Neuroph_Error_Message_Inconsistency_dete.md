---
title: "Can't run Neuroph Error Message: Inconsistency detected by ld.so: dl-lookup.c: 111: c"
date: 2019-04-22
forum: General Help
---

### Post by joesalmon1985 on 2019-04-22
I get the below output when I try to run Neuroph using the below command.

joe@joe-Latitude-E7240:~$ sudo /bin/sh "/usr/local/neurophstudio/bin/neurophstudio"
WARNING: An illegal reflective access operation has occurredWARNING: Illegal reflective access by org.netbeans.ProxyURLStreamHandlerFactory (file:/usr/local/neurophstudio/platform/lib/boot.jar) to field java.net.URL.handler
WARNING: Please consider reporting this to the maintainers of org.netbeans.ProxyURLStreamHandlerFactoryWARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Gtk-Message: 20:55:00.513: Failed to load module "canberra-gtk-module"
Inconsistency detected by ld.so: dl-lookup.c: 111: check_match: Assertion `version->filename == NULL || ! _dl_name_match_p (version->filename, map)' failed!joe@joe-Latitude-E7240:~$ A

I'm assuming the command sudo /bin/sh "/usr/local/neurophstudio/bin/neurophstudio" is the right one to give as this is the location the application icon points to. Any more info I can provide let me know.

---

