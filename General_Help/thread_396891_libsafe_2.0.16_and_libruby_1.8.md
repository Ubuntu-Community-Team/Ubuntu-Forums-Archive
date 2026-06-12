---
title: "libsafe 2.0.16 and libruby 1.8"
date: 2007-03-30
forum: General Help
---

### Post by nixclusive on 2007-03-30
Hello everybody, I have libsafe installed and configured to fire a mail whenever an access violation event occurs. I recently installed Amarok 1.4.3 from the *dapper-backports* repository. The new Amarok has scripting support and one of the script, 'Lyrics: LyricWiki v2.0' which depends on 'Ruby 1.8' happens to fire that dreaded mail with the termination of /usr/bin/ruby1.8

So is that a problem or should I go ahead and remove the libsafe protection? Lyrics are not working!!

Thanks for any help... :-)

> Libsafe violation detected on teststation at Thu Mar 29 23:05:40 2007
Libsafe version 2.0.16
Detected an attempt to write across stack boundary.
Terminating /usr/bin/ruby1.8.
    uid=1000  euid=1000  pid=9311
Call stack:
    0xb7f7f6e4  /lib/libsafe.so.2.0.16
    0xb7f7fb84  /lib/libsafe.so.2.0.16
    0xb7ecee81  /usr/lib/libruby1.8.so.1.8.4
    0xb7ecfb25  /usr/lib/libruby1.8.so.1.8.4
    0xb7ede991  /usr/lib/libruby1.8.so.1.8.4
    0xb7f18680  /usr/lib/libruby1.8.so.1.8.4
    0xb7ec951e  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed3f87  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed4a1a  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed152e  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed6fdb  /usr/lib/libruby1.8.so.1.8.4
    0xb7ee059f  /usr/lib/libruby1.8.so.1.8.4
    0xb7ec911b  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed3f87  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed4a1a  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed16a6  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed3992  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed28a7  /usr/lib/libruby1.8.so.1.8.4
    0xb7ed3441  /usr/lib/libruby1.8.so.1.8.4

---

