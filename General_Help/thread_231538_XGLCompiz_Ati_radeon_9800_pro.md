---
title: "XGL/Compiz Ati radeon 9800 pro"
date: 2006-08-07
forum: General Help
---

### Post by tk421 on 2006-08-07
Hi,

I have a default installation of Ubuntu and the graphics card Ati Radeon 9800 pro.

I have tried to install CGL using the following tutorial: [http://www.ubuntuforums.org/showthread.php?t=174233&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=174233&highlight=xgl)

I  just have changed one think. I have substitute xv:fbo by xv:pbuffer because im an ATI user ([http://www.ubuntuforums.org/showthread.php?t=174233&page=2&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=174233&page=2&highlight=xgl))

I didn't get it working. Session does not start

```

tk421@matrix:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tk421"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/matrix:/tmp/.ICE-unix/5283
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:5353): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5353): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

```

First of all, I can see here [http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards) thats is known that this works with drivers "ati-drivers-8.22.5"

I think (but not sure) that mayby the graphic card must be installed (correctly). Is this OK?

Any other ideas?

Thanks in advance.

---

