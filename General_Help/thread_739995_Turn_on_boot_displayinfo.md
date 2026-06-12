---
title: "Turn on boot display/info ???"
date: 2008-03-30
forum: General Help
---

### Post by waynep on 2008-03-30
Hi All, I have 7.10 on a HP nc4000 laptop. Things work fine, outside of the power management stuff. I have not worked on that yet. 

The issue, maybe not an issue, is that it takes forever to boot. My windows machines take less time to boot. When it boots, it sits at a blank screen until the Gnome login screen shows up.  I do get the initial boot loader timeouts etc, but then it goes to a blank screen. I would like to turn on the boot entertainment so I can see what it's doing during boot time . . . . How do I do this?

-wayne

---

### Post by y-lee on 2008-03-30
edit the grub menu list, the file **menu.lst**,  found **/boot/grub** and remove the quiet option from the kernel line the messages should  appear in the splash.

Make a backup in case you mess up using a command like:

   ```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

And edit as superuser 

```
sudo gedit /boot/grub/menu.lst
```

Save your file after you are done try rebooting.

Hope that helps :)

---

