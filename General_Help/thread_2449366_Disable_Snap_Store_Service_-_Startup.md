---
title: "Disable Snap Store Service - Startup"
date: 2020-08-25
forum: General Help
---

### Post by cedrones on 2020-08-25
Does anyone know how to disable the Snap-Store service on Startup?  I'm running 20.04 on a couple of PC's and it wastes about 500mb of memory and I see no need to keep it running when I'm not using the Snap-Store.  The memory it consumes gets worse as the computer has been up over time and I'd like to disable the service from auto-starting and just start it as needed.

Thoughts?

---

### Post by zebra2 on 2020-08-25
you can use "systemctl stop snapd" to stop it. Pretty sure you can use "systemctl stop --disable snapd" to disable it.

My favorite solution is "apt purge snapd"  which gets rid of it completely.  Other than what you mention I don't get the snap deal at all.

---

### Post by deadflowr on 2020-08-25
*Thread moved to **General Help***

---

### Post by monkeybrain20122 on 2020-08-25
If you are not using snap store then you can simply remove all snap stuffs
```

sudo apt purge snapd
```

That's it. It will remove all systemwide snap stuffs.

---

### Post by vanadium on 2020-08-27
This may be an autostart .desktop file under /etc/xdg/autostart/. I cannot check because I do not have it installed. Copy that .desktop file to your user's home directory under .config/autostart and, in the copy, add the line "Hidden=true". No root permissions needed.

---

### Post by zebra2 on 2020-08-27
@OP 
You don't say what release you are using but if it is 20.04 or later and you purge snapd you will also remove gnome-software. The result is that you will have to install deb packages from the command line or use synaptic or similar. Reinstalling gnome-software will also reinstall snapd in the later releases. PS i'm beginning to see why Arch is still popular.

---

### Post by deadflowr on 2020-08-27
> **zebra2 said:**
> @OP 
You don't say what release you are using but if it is 20.04 or later and you purge snapd you will also remove gnome-software. The result is that you will have to install deb packages from the command line or use synaptic or similar. Reinstalling gnome-software will also reinstall snapd in the later releases. PS i'm beginning to see why Arch is still popular.

gnome-software is one thing snap-store is another.
uninstalling snapd removes snap-store. it has no bearing on gnome-software.
If the OP has gnome-software installed, it'll stay installed.
gnome-software shows as Software in Applications listings.
snap-store shows as Ubuntu software in Application listings.

---

