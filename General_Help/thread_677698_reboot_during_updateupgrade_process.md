---
title: "reboot during update/upgrade process"
date: 2008-01-25
forum: General Help
---

### Post by xaknafein on 2008-01-25
I tried updating my ubuntu via adept. At some point it prompted that a new distro is available and I chose to download it.

During the download, at the "Installing new apps" stage (or something similar) the install was stalled. Roughly 20 minutes without any progress (stuck at 0%).
At this point I rebooted the computer (might have been stupid!).

Currently things are not as they should be.

sudo dpkg --configure -a 
returns:
dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 2 package `libc6':
 `triggers-pendi' is not allowed for third (status) word in `status' field

I have (at the suggestion of others) tried various commands such as
apt-get -f install
apt-get update
and a few others.
All return with:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

The result of which has already been outlined.

I'm wondering, how can I fix this? Is there some way to restart the whole update process all over again? I tried running adept again but it says that another process is using the update manager and I need to exit that, but I have no idea what that other process might be.

---

### Post by jken146 on 2008-01-25
> E: dpkg was interrupted, you must manually run '**dpkg --configure -a**' to correct the problem.
Have you done what it suggested?

---

### Post by zivxx on 2008-01-25
sudo dpkg --configure -a 
returns:
dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 2 package `libc6':
 `triggers-pendi' is not allowed for third (status) word in `status' field

yes he have..


hey im not that expert but it looks like you got a valid package

try ```
nano /var/lib/dpkg/updates/0003
```

then delete the valid package it tells you then run again ```
sudo dpkg --configure -a
```

and i believe it should work..not sure tho

---

### Post by xaknafein on 2008-01-25
Thanks, your post helped. I think i have it fixed now.

---

