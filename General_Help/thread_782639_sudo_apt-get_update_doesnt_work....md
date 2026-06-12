---
title: "sudo apt-get update doesnt work..."
date: 2008-05-05
forum: General Help
---

### Post by zasten on 2008-05-05
Hi,

When I issue the command "sudo apt-get update" I get the following error message.

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

However I can reload in synaptic or if I switch to root the I can update the cache.

Do I have an sodoer problem? Other commands that require root privaliges work. e.g. sudo gedit /boot/grub/menu.lst

How do I fix this?

/thanks zasten

---

### Post by enbuyukfener on 2008-05-05
That is usually only a problem when you have two package management utilities running simultaneously, e.g. using apt-get update when synaptic is already running.

I think I recall one incident where this error popped up unexpectedly and I restarted X to solve the problem so maybe just try that. If the problem occurs again, it may be a sign of a bigger problem, in which case, report back.

---

