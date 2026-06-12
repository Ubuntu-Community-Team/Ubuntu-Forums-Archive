---
title: "I log in then get logged right back out"
date: 2006-09-02
forum: General Help
---

### Post by brentrussell on 2006-09-02
I installed xubuntu then installed gnome and have been using gnome fine for a few days. Now when I log into gnome it starts to load the desktop then without warning it cuts to command line (looks like init 3) and asks me to log in. whether I log in or not it goes back to the X login screen after 5-20 seconds (completley random)

When I log in the second time (using the X Windows Login), it goes to an xfce session and I get the follwing error displayed:
Your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

The details section of the error states:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "russellb"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/1leghampster:/tmp/.ICE-unix/5530
** (nautilus:5605): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS
** (nautilus:5605): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS
** (nautilus:5605): WARNING **: Can not get _NET_WORKAREA
** (nautilus:5605): WARNING **: Can not determine workarea, guessing at layout
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

I have plenty of disk space on all partitions including swap.
I read some place online where someone had an error sort of like mine and they did the following but it did not work for me
sudo chown russellb /home/russellb/.ICEauthority
sudo chmod 600 /home/russellb/.ICEauthority
I also tried setting the perms to 777. When I made a backup of the file and deleted the original.... the file was remade and I recieved the same results

After logging in after about 4 times to gnome it just magicly works and I have NO problems UNTIL I reboot or try to log out and log back in.
Any help is greatly appriciated.

---

### Post by brentrussell on 2006-09-02
I have taken out everything from my .bashrc_aliases and took out my networked drives in fstab plus completley unplugged all of my attached devices such as removable hard drives.

---

### Post by brentrussell on 2006-09-03
Found more information in /home/russellb/.xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "russellb"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/1leghampster:/tmp/.ICE-unix/5607
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(tilda:5699): Gdk-CRITICAL **: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by brentrussell on 2006-09-03
Disabled tilda and I am getting these errors in /home/russellb/.xsession-errors and the original problem still exists

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "russellb"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/1leghampster:/tmp/.ICE-unix/7198
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:7271): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -19 and height 25

(gnome-terminal:7384): Gdk-CRITICAL **: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (gnome-terminal:7384): WARNING **: No handler for control sequence `device-control-string' defined.

** (nautilus:7273): WARNING **: file already in tree (parent_ptr: (nil))!!!

---

### Post by brentrussell on 2006-09-05
Anyone help me out on this? I just did a fresh install of xUbuntu, installed the gnome desktop and started using gnome and it started again after the first login. I am lost and have no idea where to start next. Anyone help?

---

### Post by brentrussell on 2006-09-09
Reinstalled

---

### Post by whitetreebark on 2007-04-17
This same thing happens to me.  Edgy began doing this very suddenly (after having worked smoothly for several months). After logging in, it loads for a few seconds, the screen flashes, there is blankness for a while, then right back to the login screen.  I have yet to find the reason...  (possibly from some automatic update?)

---

### Post by aquilonis on 2007-04-19
A similar thing happened to me as well and I have similar errors in the .xsession-errors file. For me, gnome did launch (sort of). Kind of like gnome-meets-alice-in-wonderland though (window control shot; workspaces gone; etc)

Strange behavior started appearing 2 days ago when sound stopped working. Today was my first reboot since that time. Windows (XP) works fine, including sound.

After much screwing around, I was able to recover gnome by creating a new user and logging in there (.gome worked for the new user). I then deleting everything in my home directory that appeared to have something to do with gnome startup (basically, .g*). 

This was easier than re-installing, but very disconcerting, esp. as sound is still out   :-/

I'm running 7.04 beta. This is a major bug.

---

### Post by Omegatron on 2007-04-29
I am getting a similar problem after the computer's power was cut.  I can't log in through the regular sessions.  It pops up a box that says:

> 
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "omegatron"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Inspiron:/tmp/.ICE-unix/6407
Initializing gnome-mount extension

(gnome-panel:6468): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 25

(nm-applet:6476): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6477): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6483): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6478): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6485): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evince:6486): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6475): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

There isn't an actual ~/.xsession anything file though.

If I try to log in again, it brings back the session that I was running when power was cut, but it also pops up that box, and if I click "Ok" it crashes and logs out.  If I click the shutdown icon it crashes gnome-panel.  Even if I restart gnome-panel from a terminal, clicking the shutdown icon crashes it.

I think it has something to do with restoring the last saved session.  I've tried to delete the saved session but I don't really know how.

If I run a failsafe session it works fine.

---

### Post by Omegatron on 2007-04-29
I renamed ~/.gnome2/session and ~/.gconfd/saved_state and it seemed to work?  We'll see...

---

### Post by Omegatron on 2007-04-29
Ugh.  Now I've permanently lost my window decorations, but it doesn't crash anymore.

---

### Post by Omegatron on 2007-04-29
i ran metacity from a terminal and then metacity --replace from another terminal and it seems to remember to run the window manager now :-(

Who knows what underlying non-visual things are still broken, though?

---

### Post by Omegatron on 2007-04-29
Nope.  Still broken.

---

