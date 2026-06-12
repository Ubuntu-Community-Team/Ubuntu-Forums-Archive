---
title: "now cant log on, started with gnome panel crash?"
date: 2008-06-04
forum: General Help
---

### Post by darkline on 2008-06-04
A couple minutes ago ubuntu crashed after i opened the places menu, the icons didnt load, and then everything froze until i pressed ctrl+alt+backspace.

The same thing happened again after logging in again. and when i went on places after adding a new main menu. Going to bookmarks, and the side panel worked perfectly fine on nautilus.

After using a new main menu, i now cannot log onto any session except for the failsafe terminal, xclient script, gnome and failsafe gnome all do not work. All the others play the music, and start to load, but the screen goes black before my wallpaper even comes up.


Has anyone got any ideas?
Any logs i can post that will help?

I am using gutsy, if that makes a difference.

---

### Post by prince_niceguy on 2008-06-04
Try login in the failsafe mode. if that does not work out then try resetting your gnome profile. You can do same by logging into the fail-safe terminal and running the following code

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

hope that helps.

---

### Post by darkline on 2008-06-04
I tried the code in the failsafe termnial, and it hasnt helped unfortunatly.

I tried logining in failsafe gnome, and it came up with a warning about only using it to fix problems, i presed ok, then the screen went blank, and the login music played.


I have also now logged in with another user (now ive got the password for it!), on this account everything works perfectly. Ecept that if i open the places menu it crashes.
Im gonna have to avoid it, because i would like to continue to be able to log in!

---

### Post by prince_niceguy on 2008-06-04
There would be a .Xsession errors file in your home directory. can you share the same.

Any reason you are not upgrding to hardy? I would recommend an upgrade as lots of bugs are fixed in new version of gnome in hardy which is not there in gutsy.

---

### Post by darkline on 2008-06-04
the .xsessionerrors file:

(process:10113): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:10117): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/h3n-desktop:/tmp/.ICE-unix/10110


I have no real resons for upgrading, other than i was under the impression a few errors can happen when upgrading, and at the moment a kinda busy, so i didnt want to take the time to do it yet.

---

### Post by darkline on 2008-06-04
ok, i just accidently opened the places menu in this account, and it crashed again:( 

when i logged back in the gnome pannels werent there for  some reason

the .xsessionerrors for this account now.(the last one is where i cant login at all)::
(process:11858): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:11862): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/h3n-desktop:/tmp/.ICE-unix/11855
A panel is already running.
Checking for Xgl: not present. 
Initializing gnome-mount extension
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: 
** (nautilus:11904): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11904): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11904): WARNING **: Can not get _NET_WORKAREA

** (nautilus:11904): WARNING **: Can not determine workarea, guessing at layout
present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:12015): WARNING **: Tracker daemon is already running - exiting
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 16054 1212624000 1212607946
evolution-alarm-notify-Message:  Thu Jun  5 01:00:00 2008

evolution-alarm-notify-Message:  Wed Jun  4 20:32:26 2008

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
  PID TTY          TIME CMD
** Message: Error: Could not determine type of stream.
gsttypefindelement.c(735): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couln't open file 'file:///home/h3n/skiffs.mpg'
Reason: Could not determine type of stream..

---

### Post by prince_niceguy on 2008-06-04
try disabling compiz for the time being and see if it solves the issue. it may be a compiz bug. not sure.

---

### Post by darkline on 2008-06-04
hmmm, how would a be able to disblle compiz when i cant login?

I can try with the one that has lost the panels though:)

---

### Post by darkline on 2008-06-04
well, i can now log in on the old account, i dont know what has happened there tho:S

And unfortunatly disabling compiz doesnt help, although i found that killing the process dbus-daemon solved all the problems.

I have just found it crashes as well when i open up system tools group in the applications menu. Maybe its somin to do with the icons or something, coz they never show up, the writing does and everything, but theres no icons.

This is really confusing


edit: also have found changing the theme fixes the problem, which is probably why stopping the daemon helped, as that made it change theme. I suppose ill just have to reinstall the old theme or use a different one from now on.

---

