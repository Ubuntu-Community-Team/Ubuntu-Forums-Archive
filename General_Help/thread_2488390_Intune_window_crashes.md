---
title: "Intune window crashes"
date: 2023-07-04
forum: General Help
---

### Post by di-mk1 on 2023-07-04
Hello,

my organization requires us to enroll our devices to Intune for security reasons. When I launch Intune from the terminal I get the following error:

```
~$ intune-portal 
2023-07-04 11:28:02  INFO Command line arguments args=PortalArgs { common: CommonArgs { interactive: false, socket_path: "/run/intune/daemon.socket" } } version="1.2305.20"

(intune-portal:37748): Gtk-WARNING **: 11:28:02.079: Duplicate child name in GtkStack: page2
2023-07-04 11:28:06  INFO Starting a new login
2023-07-04 11:28:06 ERROR oneauth{tag="5zt6o"}: (Code:2604) Network infrastructure failure.
2023-07-04 11:28:06 ERROR oneauth{tag="69x1u"}: UI web navigation failed
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted (core dumped)

```
I have tried setting a new locale (using EN, DE, and GR) but none seems to do the trick. Any idea? Running on Ubuntu 22.04.

---

### Post by Xian on 2023-07-04
Try running this terminal command and then relaunch program:

```
export LC_ALL=C
```

For why this might be helpful see [https://unix.stackexchange.com/questions/87745/what-does-lc-all-c-do](https://unix.stackexchange.com/questions/87745/what-does-lc-all-c-do)

---

