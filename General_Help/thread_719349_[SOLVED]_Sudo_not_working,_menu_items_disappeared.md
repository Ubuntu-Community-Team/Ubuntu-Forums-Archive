---
title: "[SOLVED] Sudo not working, menu items disappeared"
date: 2008-03-09
forum: General Help
---

### Post by linuxfault on 2008-03-09
Hello,
I installed Ubuntu 7.10 on my desktop (Dell Dimension 3000). 2 days later menu items such as the Add/Remove, Synaptic package manager etc disappeared. Also, sudo is not working at all. It's installed but it doesn't work and i don't get any errors.
I tried adding the menu items back through Preferences > Main Menu, but as soon as i check something it unchecks by itself. I did add my username under admin in /etc/group, fixed the sudoers file and also fixed the /etc/hosts file. Nothing has worked, no sudo, no menu items. Any help would be appreciated.

Thanks, 
Stan

---

### Post by Super TWiT on 2008-03-09
Did you do anything before they started disappearing?  It sounds like either the directory for your home folder isn't right or that .gnome or something similar got deleted.  I had this happen to me when I tried to change my home directory, but deleted the current one I was using before the change was complete.

---

### Post by taurus on 2008-03-09
Let's see what groups you do really belong to.  Open a terminal and post the output of this command.

```
id
```

---

### Post by linuxfault on 2008-03-09
I fixed it, thanks everyone. usermod did not work apparently, so i just booted in recovery mode and added me under admin, everything is fine now.

---

### Post by linuxfault on 2008-03-09
> **Super TWiT said:**
> Did you do anything before they started disappearing?  It sounds like either the directory for your home folder isn't right or that .gnome or something similar got deleted.  I had this happen to me when I tried to change my home directory, but deleted the current one I was using before the change was complete.

no i did not do anything, i got back from work and it was messed up. thanks though

---

