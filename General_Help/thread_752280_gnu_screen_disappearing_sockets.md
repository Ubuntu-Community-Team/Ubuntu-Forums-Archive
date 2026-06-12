---
title: "gnu screen disappearing sockets"
date: 2008-04-11
forum: General Help
---

### Post by baxrob on 2008-04-11
Hi there,

Since switching to Gutsy from Dapper, my screen sockets have been getting deleted on reboot.  Under Debian, and Ubuntu Dapper, I was accustomed to sockets sticking around pretty much no matter what.

I've tried changing the socket directory (from /var/run/screen to ~/.screen), running screen suid (not that that would affect this, i suppose), and explicitly setting "autodetatch on" in /etc/screenrc, but none of this has helped.  My google-fu has failed me so far on this one.

I don't see any bug reports on launchpad ([https://bugs.launchpad.net/screen/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=screen](https://bugs.launchpad.net/screen/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=screen))

Any ideas?  Anyone else get this behavior?

TIA,
Rob

---

