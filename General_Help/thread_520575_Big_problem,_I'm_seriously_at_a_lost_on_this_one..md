---
title: "Big problem, I'm seriously at a lost on this one."
date: 2007-08-08
forum: General Help
---

### Post by blithen on 2007-08-08
when I log into ubuntu I get this
```

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Process /usr/lib/control-center/gnome-settings-daemon received signal 11

GNOME will still try to restart the Settings Daemon next time you log in.
```
I'm still able to use Gnome, and everything else. Just it's very bland, and not normal.

---

### Post by apetresc on 2007-08-08
Check the myriad of workarounds suggested on this bug: [https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)

The basic idea boils down to a problem in /etc/hosts and/or /etc/network/interfaces . Fixing those resolved the bug for a lot of people, hopefully it helps you too!

The main seems to be this: make sure the line ```
auto lo
``` appears in your /etc/network/interfaces file. (Preferably with lines after it specifying address and netmask)

For other people, commenting out the IPv6 addresses in /etc/hosts helped. Some people did both.

---

