---
title: "[SOLVED] Borked Desktop"
date: 2007-12-20
forum: General Help
---

### Post by Greasyfingers on 2007-12-20
I've been trying out different file managers in Gutsy to replace Gnome's default Nautilus, and have messed up my desktop. On bootup I get a black screen with the desktop icons arranged in rows and unmovable - no background, and no configuration is possible; a sort of empty void of a desktop (though the panels work OK). If I log out and back in again, *usually* the full desktop returns, along with this error message:
> 
GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running.  Desktop environment like GNOME or XFCE automatically execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0. (create it if no such file)

NOTICE: The icon theme you choose should be compatible with GNOME, or the file icons cannot be displayed correctly.  Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used.  Currently there is no standard for this, but it will be solved by freedesktop.org in the future.

*Sometimes* closing this message box takes the desktop away with it again, but usually it is OK from then until next I boot. The desktop seems to be the only thing affected.

Can anyone help with a fix, please?

---

### Post by yabbadabbadont on 2007-12-20
You will need to tell us what, exactly, you have done.  :)

---

### Post by PeterJS on 2007-12-20
Looks like the gnome settings manager isn't loading up like is should when you login in. Try this:

Go to System > Preferences > Session. There's a button to add a new application to load with the desktop. If you add a new entry for the command *gnome-settings-daemon* that should start it when you log in. This isn't the Right Way(tm), but it should fix the problem.

---

### Post by Greasyfingers on 2007-12-20
'S OK guys, I seem to have it fixed.

I've tried out several different file managers over the past few days, and started off following the instruction on [_[color=blue]this page[/color]_]("http://www.psychocats.net/ubuntu/nonautilusplease"). Although I ran the restorenautilus.sh script, I realised that the folders on my broken desktop were still opening with Thunar. ```
sudo apt-get remove thunar
``` fixed things.

Thanks

---

