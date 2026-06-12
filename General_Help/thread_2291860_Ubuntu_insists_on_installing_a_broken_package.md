---
title: "Ubuntu insists on installing a broken package"
date: 2015-08-23
forum: General Help
---

### Post by Novitk on 2015-08-23
Everytime I boot the system, I receive a "System crash" message and here is the details:

[IMG]http://i.imgur.com/ovfEhvd.png[/IMG]

This package is already removed, but Ubuntu insists on trying to install it everytime I boot the system. What's going on exactly and how do I fix this error?

---

### Post by ian-weisser on 2015-08-24
Look for the appropriate .crash file in /var/crash
Attach the .crash file to this thread.

---

### Post by v3.xx on 2015-08-24
You could also remove the /var/crash/apport file and see if it gets recreated.  Sometimes apport will just get stuck on a old crash.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

