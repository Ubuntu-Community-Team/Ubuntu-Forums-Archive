---
title: "Hidding the mounted disks"
date: 2008-07-09
forum: General Help
---

### Post by ttry72 on 2008-07-09
I have disk partitions mounted (approx 7) in Gutsy Gibbon. The issue is, that I dont want to show them desktop users, only admin/root should be able to see them.


How can I hide some of the mounted disks from other users? This is little annoying for desktop users, because all 7 mounting points are on their desktop.

---
***The case is solved. Thank you for the contribution!***

---

### Post by Vivaldi Gloria on 2008-07-09
> **ttry72 said:**
> I have disk partitions mounted (approx 7) in Gutsy Gibbon. The issue is, that I dont want to show them desktop users, only admin/root should be able to see them.


How can I hide some of the mounted disks from other users? This is little annoying for desktop users, because all 7 mounting points are on their desktop.

If you mount them to /mnt/mountpoint via fstab then they don't show icons on the desktop. Then you can put a symlink to where ever you want.

---

### Post by crossedout on 2008-07-09
You could also just change the volumes_visible preference in gconf.

-Xout

---

### Post by Vivaldi Gloria on 2008-07-09
> **crossedout said:**
> You could also just change the volumes_visible preference in gconf.

-Xout

Changing that in gconf-editor also works but there is a problem with it: cd's and usb disks don't show up on the desktop anymore.

---

### Post by crossedout on 2008-07-09
> Changing that in gconf-editor also works but there is a problem with it: cd's and usb disks don't show up on the desktop anymore.

Vivaldi is correct.  I suggested gconf b/c I got the impression having any form of mounted device show on the desktop was unacceptable.  Keep in mind, changing the volumes_visible preference will still leave them visible through nautilus.

-Xout

---

### Post by ttry72 on 2008-07-09
> **Vivaldi Gloria said:**
> If you mount them to /mnt/mountpoint via fstab then they don't show icons on the desktop. Then you can put a symlink to where ever you want.

Thanks, I'll try that. About the gconf, I have no idea how to use it...

---

### Post by Vivaldi Gloria on 2008-07-09
> **ttry72 said:**
> Thanks, I'll try that. About the gconf, I have no idea how to use it...

Press Alt+F2 and start 

```
gconf-editor
```

Then look at the key

```
/apps/nautilus/desktop/volumes_visible
```

---

### Post by ttry72 on 2008-07-09
> **Vivaldi Gloria said:**
> Press Alt+F2 and start 

```
gconf-editor
```

Then look at the key

```
/apps/nautilus/desktop/volumes_visible
```

Thanks! The case is solved. Actually I mounted the disks under /mnt directory so they are avalaible but not visible.

---

