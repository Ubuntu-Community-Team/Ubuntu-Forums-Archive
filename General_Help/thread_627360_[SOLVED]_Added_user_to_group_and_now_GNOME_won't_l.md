---
title: "[SOLVED] Added user to group and now GNOME won't load...."
date: 2007-11-30
forum: General Help
---

### Post by ZachSka87 on 2007-11-30
I added my username to the VM users group that VirtualBox installs and now Gnome doesn't load when I log in.  Is there a way to remove myself from that group from the command line?

---

### Post by ZachSka87 on 2007-11-30
Fixed...don't know why adding me to a group did this, but it did.

sudo nano /etc/group

I removed my username from the group line

---

