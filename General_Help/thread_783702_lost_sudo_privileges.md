---
title: "lost sudo privileges"
date: 2008-05-06
forum: General Help
---

### Post by GOwin on 2008-05-06
I'm using Hardy 64-bit. It was running fine until I noticed that I'm running out of /var space. So I decided to boot using  wolvix livecd and use the gparted from there.

Everything seems working fine until I decided I need to run apps with root privileges. Now, I can't run them. I also noticed that I can loss the "Add/Remove software" option from the gnome menu. Basically, anything that has to do with root privileges.

Has anyone encountered this? What's the fix?

---

### Post by tamoneya on 2008-05-06
boot into recovery mode by hitting escape when grub loads.  Then you will be booted into a CLI interface with root privileges.  From here you need to readd your user to the admin group: ```
usermod username -g admin
```

---

