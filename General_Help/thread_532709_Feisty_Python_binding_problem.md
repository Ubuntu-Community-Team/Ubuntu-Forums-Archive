---
title: "Feisty: Python binding problem"
date: 2007-08-23
forum: General Help
---

### Post by myst12345 on 2007-08-23
Hi,

Since an update a little while ago I have not been able to run a number of Python/GTK apps.

beryl-settings, and gnome-app-install are 2 examples.
Failing with variants of :

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 22, in <module>
    import berylsettings
ImportError: /usr/lib/libX11.so.6: undefined symbol: XdmcpWrap

Sounds less like a missing package then something has changed with the bindings?

Any help would be appreciated.

Cheers

---

### Post by myst12345 on 2007-08-25
Ok, so I stopped being lazy and had a dig around.

One thing I noticed was that after installing various debs i'd get an ldconfig error saying libXdmcp.so.6 wasn't a symlink.

$ dpkg -s libXdmcp.so.6
libxdmcp6: /usr/lib/libXdmcp.so.6.0.0

sudo apt-get install --reinstall libxdmcp6

And now all is well. Hope that helps anyone else who might have the same.
No idea how it got messed up in the first place though.

Cheers
Mitch

---

