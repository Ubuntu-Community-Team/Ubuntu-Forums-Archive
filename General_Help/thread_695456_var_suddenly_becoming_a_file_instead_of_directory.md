---
title: "/var/ suddenly becoming a file instead of directory"
date: 2008-02-13
forum: General Help
---

### Post by steffen on 2008-02-13
After going into hibernation, X.org won't start. Turned out that when I looked into my directory structure, the whole /var/ directory was marked as a **file** not a directory. I have no idea how this happened. I did not run anything as root before the hibernation, so I shouldn't even have been able to touch it. This is a 100% Ubuntu installation, installed as edgy and dist-upgraded to gutsy last October, with no third-party addons.

An "ls -la" returns "-rw-r--r--" as permissions for /var

1. How did this happen? I have used Linux for five years, and not yet come across this.

2. How can I make /var/ recognisable as a directory again, and not a file?

I would probably be able to rebuild /var/ from scratch, but that's not what I want to do. I'd like to find out how/why this happened and how I can fix it properly.

Thanks to anyone with a suggestion!

---

