---
title: "Problems with Firestarter packet logging going to system console"
date: 2005-04-30
forum: General Help
---

### Post by rlcarr on 2005-04-30
I've installed firestarter and it's running great with respect to filtering, etc.

However, for some bizarre reason, when it logs blocked packets, the packet log not only goes to the appropriate files in /var/log, but they also go to the system console and I am at a total loss to figure out why.  My /etc/syslog.conf is what Hoary installed (I haven't made changes to it) and /dev/console is **nowhere** mentioned in it.  And nothing else is going to the system console except for the packet logs.

Anyone have any idea what's going on?

---

