---
title: "/snap/bin in PATH but directory does not exist"
date: 2019-12-08
forum: General Help
---

### Post by Skaperen on 2019-12-08
in Xubuntu i discovered that the default PATH (which i usually do not use, but sudo does) includes /snap/bin which does not exist.  is this the normal way of SNAP, to leave it non-existent until a Snap is installed?

---

### Post by spjackson on 2019-12-11
You get /snap/bin in your path because of  /etc/profile.d/apps-bin-path.sh which is provided by the snapd package. I  believe that recent versions of all Ubuntu flavours, including Server  (don't know about Minimal) install snapd by default. So what you see is  not limited to Xubuntu. Ubuntu Desktop installs some snaps and you get  the /snap/bin folder containing some links.

You should have a /snap/README, though that doesn't shed much light on  how /snap/bin gets created - I'd guess that installing any snap would do  it.

---

### Post by #&amp;thj^% on 2019-12-11
In a default install of Xubuntu "snapd " has been installed with the .iso
Snapd= (A Service and tools for management of snap packages)
snapd ships a snippet in /etc/profile.d that sets the PATH to /snap/bin and should theoretically work for all login shells (except for zsh which doesn't respect the profile.d standard).
You get somewhat of a idea with:
```
systemd-path search-binaries
```
As it sits currently, I shed snaps and snapd as fast as I install any buntu system.
```
# env | grep PATH
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
MOZ_PLUGIN_PATH=/usr/lib/mozilla/plugins
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/lib/jvm/default/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/usr/lib/jvm/default/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/var/lib/snapd/snap/bin

```
For the above output I just installed snapd temporarily.
And:
```
# env | grep PATH
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
MOZ_PLUGIN_PATH=/usr/lib/mozilla/plugins
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/lib/jvm/default/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/usr/lib/jvm/default/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/var/lib/snapd/snap/bin

```
There has been a few bugs opened recently about how the paths have been set, with mentions of systemd.
I'm not sure if your just making a statement or asking for support here.

---

### Post by Skaperen on 2019-12-11
if it creates the directory when it needs to put a symlink in there, then it should be good.  i'm just not used to unix-like stuff doing that (no directory until needed) even though i have done things that way myself.  i have .bashrc code that removes PATH directories that do not exist.  i'll need to add some code to detect it, or make a list of exceptions (or directories to always have in PATH).

---

