---
title: "Enable restricted driver in command line"
date: 2008-01-19
forum: General Help
---

### Post by derek_1284 on 2008-01-19
Hi-

I'm new to Ubuntu and Linux in general. Today I was just trying some things and I unchecked the enable box in the Restricted Drivers Manager for my ATI graphics card. It prompted for a reboot, but now I get an error just a few seconds after logging in  as it is trying to load the desktop. Then it just takes me back to the login prompt again.

Here are the details of the error:

(process:5361): Gtk-WARNING **: This rocess is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead.

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present.
Starting Xgl with options: -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp - fullscreen -br +xinerama
Warning, xpress200 detected.
Could not init font path element /user/share/fonts/x11/tif/, removing from list!
FreeFontPath: FPE " /user/share/fonts/x11/misc/" refcount is 2, should be 1; fixing.
...

The error goes on further, but let me know if you need more. It goes on to say things like:
The application ' * ' lost its connection to the display :2.0; most likely the X server was shut down or you killed/destroyed the application.

Right now I only have access to the command line in the recovery mode, and I'm wondering if there's a way to re-enable that restricted driver that I really shouldn't have disabled.

Any help will be greatly appreciated.

---

### Post by pointone on 2008-01-19
Try running the command "dpkg-reconfigure xserver-xorg". This will regenerate an xorg.conf file; one that doesn't try to load the disabled driver. Afterwards, you'll be able to get back into X and fix things the GUI way.

---

### Post by PeterJS on 2008-01-19
> **derek_1284 said:**
> Hi-

I'm new to Ubuntu and Linux in general. Today I was just trying some things and I unchecked the enable box in the Restricted Drivers Manager for my ATI graphics card. It prompted for a reboot, but now I get an error just a few seconds after logging in  as it is trying to load the desktop. Then it just takes me back to the login prompt again.

Here are the details of the error:

[b](process:5361): Gtk-WARNING **: This rocess is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead.

Refusing to initialize GTK+.[/b]
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present.
Starting Xgl with options: -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp - fullscreen -br +xinerama
Warning, xpress200 detected.
Could not init font path element /user/share/fonts/x11/tif/, removing from list!
FreeFontPath: FPE " /user/share/fonts/x11/misc/" refcount is 2, should be 1; fixing.
...


So here's what the source of that error is, when you uninstalled the restricted driver the Restricted Driver Manager was running with elevated privileges, and when the system shutdown to reboot the Restricted Driver's Manager was saved by the session manager. Now when you try to login the session manager is trying to reload all the applications you had open when the system shut down, including the restricted drivers which was running with elevated privileges, and the session manager does the security correct thing and doesn't load restricted drivers manager, which results in the session failing to load.

If you login on one of the physical consoles, or use the fail safe session, once there delete  ~/.gnome2/session, this will clear the session data, and when you login in to gnome again it will be a brand new session and the restricted driver manager won't try and fail to load.

---

### Post by derek_1284 on 2008-01-19
Generating a new xorg.conf file fixed the problem. Thanks!

---

