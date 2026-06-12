---
title: "Screenlets not running properly in Hardy"
date: 2008-05-05
forum: General Help
---

### Post by Aetheric on 2008-05-05
Hi all,

This is about the strangest bug I've come across. I'm trying to get screenlets 0.1.1 running on Ubuntu Hardy 64bit, but every time I try to start one from the screenlets-manager nothing happens or I get a bug report saying that Screenlets crashed unexpectedly.

I can get the screenlets themselves to run, but only if I run them with sudo through the terminal which makes the screenlets-manager daemon run as root. The manager has no functionality when it's run as root, and I can't do anything with the screenlets themselves other than have them on the screen.

This seems like I'm doing something wrong with permissions somewhere, but damned if I can figure out where. The screenlets do work as far as I can tell.

Anyone seen this before? Any help is most appreciated.

---

### Post by Aetheric on 2008-05-05
Bump - can some computer genius give me any hint on how to fix this?

---

### Post by Aetheric on 2008-05-06
Ok, by a roundabout route I figured it out and fixed it.

I had to change the permissions on /usr/share/screenlets and /usr/share/screenlets-manager to allow all users read and write access. chmod wasn't working, so eventually I had to sudo nautilus, navigate to each screenlet .py file, and change the permissions directly.

I figured this out when I couldn't run alacarte except as root, and then spotted in traceback that there was an error like "IOError: [Errno 13]" and permission denied for a file in /usr/bin. So when I searched online for a solution, I spotted a thread in the forums that listed how to change the permissions.

Marking this one as solved, but if anyone else is reading this - please be very, very careful what you do if you're running nautilus as root.

---

