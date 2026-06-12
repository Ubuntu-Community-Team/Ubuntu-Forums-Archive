---
title: "edgy icons on desktop"
date: 2006-11-02
forum: General Help
---

### Post by bigal50 on 2006-11-02
I did a fresh install of edgy and unlike other versions of Ubuntu that I have installed icons for the partitions show on the desktop. I have gotten use to having a clean desktop. So my question is how can I get rid of these? I tried deleting them and the system wouldn't let me.

Thanks
Allen

---

### Post by ~LoKe on 2006-11-02
gconf-editor -> nautilus.  Untick the boxes relating to icons.

---

### Post by bigal50 on 2006-11-02
All that I could find was volumes_visable which was already unchecked. The icons that are showing are sda2 sda4 & 1 called DellUtility, it's a laptop.

---

### Post by Ramses de Norre on 2006-11-02
Then it are probably just symlinks which you can simply remove.
If not: what's the output of ```
ls -la ~/Desktop
```

And are you sure all the boxes in  ```
gconf-editor /apps/nautilus/desktop
``` are unchecked?

---

### Post by bigal50 on 2006-11-03
Then it are probably just symlinks which you can simply remove.
Not sure how to do this..

Here's the output from ls la ~/Desktop

allen@allen-laptop:~$ ls -la ~/Desktop
total 8
drwxr-xr-x  2 allen allen 4096 2006-10-31 22:38 .
drwxr-xr-x 29 allen allen 4096 2006-11-03 09:19 

Yes all the boxes are unchecked. The show trashcan icon was checked but it didn't show on desktop, it to is unchecked now

---

### Post by HeWhoWalks on 2006-11-04
> **bigal50 said:**
> 
Here's the output from ls la ~/Desktop

allen@allen-laptop:~$ ls -la ~/Desktop
total 8
drwxr-xr-x  2 allen allen 4096 2006-10-31 22:38 .
drwxr-xr-x 29 allen allen 4096 2006-11-03 09:19 


Are you sure you copied all the output from that command?  From the second line, there should be 8 items in the list.  If you only saw two items, perhaps you could try:

```
sudo ls -la ~/Desktop
```

...and see if that shows anything different.

> **bigal50 said:**
> 
Yes all the boxes are unchecked. The show trashcan icon was checked but it didn't show on desktop, it to is unchecked now

This is also pretty odd.  I don't suppose you tried rechecking and unchecking the volumes_visible checkbox in gconf-editor -> /apps/nautilus/desktop?

And if that doesn't work... you should be able to have the icons removed by changing the mount points for your other partitions to be in /mnt instead of /media, since Ubuntu only displays icons for devices in /media by default.  If you need help doing this, please post the output of the following command:

```
cat /etc/fstab
```

and we can post instructions on how to make the required changes.

Hope something here helps.  :)

-Cameron

---

### Post by HeWhoWalks on 2006-11-04
Something else that may (or may not) help, would be to replace the appropriate config keys in gconf-editor:
```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/apps_nautilus_preferences.schemas
```

then

```
gconf-tool /apps/nautilus/desktop
```

and recheck/uncheck the volumes_visible box, along with any others you want to change the behaviour of.

-Cameron

---

