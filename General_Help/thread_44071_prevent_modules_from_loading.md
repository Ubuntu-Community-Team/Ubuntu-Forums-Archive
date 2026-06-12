---
title: "prevent modules from loading"
date: 2005-06-24
forum: General Help
---

### Post by h-chi on 2005-06-24
hi,

i was wondering if there is a clean way of preventing modules from loading during system startup.
on debian i used the modconf tool, which i can't find in the ubuntu repositories,
and it seems like it was not ported to ubuntu on purpose.


greets

h-chi

---

### Post by az on 2005-06-24
/etc/hotplug/blacklist

---

### Post by wylfing on 2005-06-24
I could be wrong about this, but I don't think /etc/hotplug/blacklist will stop a module from loading if it's in the depency tree of a module you *do* load. For example, a particular sound driver will require soundcore to be loaded. Blacklisting soundcore won't do a thing.

---

### Post by h-chi on 2005-06-24
[QUOTE=azz]/etc/hotplug/blacklist[/QUOTE]
 via the hotplug-blacklist only driver modules for existing hardware can be prevented from loading. but what about modules like ipv6 which are only kernel specific ?

---

### Post by brainsik on 2007-10-04
I believe what you want is to add a file called "blacklist.local" to /etc/modprobe.d.

This file should be formatted like:

blacklist module1
blacklist module2

See the modprobe.conf manpage for more info and/or look at the blacklist files already present in /etc/modprobe.d.

Note: I haven't personally used this before, it's just what i would try. :-)

.:. brainsik

---

### Post by schmolch on 2007-11-27
None of this works, could anyone give a correct answer please?

I put uhci_hcd and fuse into /etc/modprobe.d/blacklist and /etc/modprobe.d/blacklist.local and rebooted, they are still loaded and none of them are a dependency for another module.

---

