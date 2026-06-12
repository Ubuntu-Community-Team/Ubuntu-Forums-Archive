---
title: "Gutsy Shutdown and Restart Issues..."
date: 2008-05-01
forum: General Help
---

### Post by robelliott2125 on 2008-05-01
Hi all,

I'm hoping this is a relatively easy fix for all you out there.

When i'm clicking my shutdown button, it used to dim the rest of the screen, load the shutdown options (reboot, logout shutdown etc), but its no longer doing this.

Whats happening, is that the screen remains unchanged, no dim, no option, and it doesn't allow me to click anything else.

If anyone needs any information about my system and things, please let me know, and how to get it.  It is becoming annoying, and I just want to get it sorted.

To actually shutdown or restart, i need to ctrl alt and backspace, then click options on the login screen and restart or shutdown.

Thank you,

---

### Post by dburnett77 on 2008-05-01
> **robelliott2125 said:**
> Hi all,

I'm hoping this is a relatively easy fix for all you out there.

When i'm clicking my shutdown button, it used to dim the rest of the screen, load the shutdown options (reboot, logout shutdown etc), but its no longer doing this.

Whats happening, is that the screen remains unchanged, no dim, no option, and it doesn't allow me to click anything else.

If anyone needs any information about my system and things, please let me know, and how to get it.  It is becoming annoying, and I just want to get it sorted.

To actually shutdown or restart, i need to ctrl alt and backspace, then click options on the login screen and restart or shutdown.

Thank you,

Sounds like an ACPI corruption, which they corrected on most systems.
If someone's been monkeying around, I'd re-install.

If you want to correct, try and re-init via xorgconf.sh or another type executable.
Manual is tricky, but rc.local is a good place to start, with GREP...

---

### Post by robelliott2125 on 2008-05-01
> **dburnett77 said:**
> Sounds like an ACPI corruption, which they corrected on most systems.
If someone's been monkeying around, I'd re-install.

If you want to correct, try and re-init via xorgconf.sh or another type executable.
Manual is tricky, but rc.local is a good place to start, with GREP...

Would me upgrading to Heron fix it?

Tbh, i don't know what caused it, and would appreciate knowing.

Since i've got this reinstalled, and running how I like, i really want to avoid reinstalling, as it means I've got to use an external dvdrw, and I feel that messed up my grub when i reinstalled it, when I remove the drive.

If someone could walk me through fixing it, I would be very much obliged.

Thank you,

---

### Post by robelliott2125 on 2008-05-01
Anyone else???

Can this be fixed easily, and without the need for a reinstall?

---

### Post by -Zeus- on 2008-05-01
> **robelliott2125 said:**
> Would me upgrading to Heron fix it?

Tbh, i don't know what caused it, and would appreciate knowing.

Since i've got this reinstalled, and running how I like, i really want to avoid reinstalling, as it means I've got to use an external dvdrw, and I feel that messed up my grub when i reinstalled it, when I remove the drive.

If someone could walk me through fixing it, I would be very much obliged.

Thank you,

Upgrading to heron may very well fix it.  If it doesn't work you can always hit Alt+F2 and do one of the following:

Restart
```
sudo reboot
```

Shutdown
```
sudo shutdown -h now
```

From your post it sounds like it used to bring up the menu to select what you want?  Is it possible that power button has been changed to another function?

---

### Post by robelliott2125 on 2008-05-02
Thank you for your post Zeus!

Last night it offered me the shutdown menu.

Just incase it doesn't happen again, i'm going to make sure I learn those codes that you've advised about.

Just need to sort my bootup problem now. lol

Btw, off topic, but my Male German Shepherd is called Zeus...  Powerful name!

---

