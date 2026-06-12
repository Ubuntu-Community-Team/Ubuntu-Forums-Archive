---
title: "How can you rebuild iftab?"
date: 2007-03-01
forum: General Help
---

### Post by BrianK on 2007-03-01
I think I've found why I can't use my disk image on new machines... it appears that iftab ties an eth to a mac address (BAD, BAD IDEA!!!, imo).  Is there  a way to recreate iftab if the entries are incorrect?  Is there a way to stop the system from using iftab?

---

### Post by terminal on 2008-01-28
I am looking for the same , where the heck does ubuntu store this information :(

---

### Post by PinkFloyd102489 on 2008-01-28
Upon checking my iftab, it says "This file is no longer used and has been automatically replaced. See /etc/udev/rules.d/70-persistent-net.rules for more information."

Also, the eth0 mac line is commented out in iftab for me.


EDIT: Checking the udev rules, it binds to a MAC address also. :-/

---

### Post by BrianK on 2008-01-28
> **terminal said:**
> I am looking for the same , where the heck does ubuntu store this information :(
Not sure what info you're talking about?

if iftab still holds a mac for an eth, you can (and this is painful) boot off a cd-distro - even the ubuntu CD, I'd imagine, find the mac address (simple ifconfig should do it), then mount the drive & edit iftab.  Reboot from the HD & should be set.

No idea how to disable this feature otherwise.  I know it's possible as some computer vendors ship with Ubuntu & image to each machine (their iftab is empty).

---

