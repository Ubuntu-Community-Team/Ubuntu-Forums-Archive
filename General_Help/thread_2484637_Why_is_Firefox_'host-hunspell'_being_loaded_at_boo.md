---
title: "Why is Firefox 'host-hunspell' being loaded at boot?"
date: 2023-03-05
forum: General Help
---

### Post by robert48 on 2023-03-05
I am looking at the Ubuntu 22.04 system mount. It shows in gparted as:

/,/var/snap/firefox/common/host-hunspell

Can somebody please tell me why 'firefox' is being loaded at boot and what does host-hunspell do?

Many thanks

---

### Post by deadflowr on 2023-03-05
Firefox isn't being loaded at boot.

The mount /var/snap/firefox/common/host-hunspell is a bind mount of the system's hunspell package.
Hunspell is a dictionary program.

It's a workaround so Firefox has access to the system's dictionary.

It's done this way because snaps don't typically have access to system files,
and so it is easier to set it up like this than to package the snap with the dozens of dictionary packages for the dozens of languages it supports,
just so a user can use only one.

You can dig through the rabbit hole here:
[https://forum.snapcraft.io/t/sdb5-mounted-on-firefox/31897/7]("https://forum.snapcraft.io/t/sdb5-mounted-on-firefox/31897/7")
[https://bugzilla.mozilla.org/show_bug.cgi?id=1732755]("https://bugzilla.mozilla.org/show_bug.cgi?id=1732755")
[https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210/93]("https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210/93")
[https://forum.snapcraft.io/t/desktop-allow-access-to-host-hunspell-dictionaries/2598]("https://forum.snapcraft.io/t/desktop-allow-access-to-host-hunspell-dictionaries/2598")

---

### Post by robert48 on 2023-03-05
Many thanks deadflowr, most illuminating. Hole in one!

---

