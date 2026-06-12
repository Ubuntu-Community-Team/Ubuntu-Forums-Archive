---
title: "Log in issues, (also displays on log out)"
date: 2008-03-30
forum: General Help
---

### Post by Klonoa on 2008-03-30
:confused:This is extremely strange, and is giving me quite a headache.:confused: When I turned on my computer it got to the log in screen fine and then I logged in, then it appeared to be logging in after It said to kill Bonobo and restart Nautilus, and then BAM, rainbow colored lines all over the screen and back to the log in screen, then I logged in in failsafe Gnome... tried to figure it out, then logged of but right before it logged off BAM rainbow lines again. I restarted the computer and tried to log in, regular Gnome, and BAM just a black screen back to the title. Does anyone have ANY idea whats going on... I'm kinda a noob so help a noob out please.

---

### Post by DoctorMO on 2008-03-30
Hmm, the graphics card might be causing problems. What card do you have? what driver are you using? what do the Xorg.log file say? in /var/log/

The problem may be that your hardware is failing (read broken), it may also be that the drivers are not quite doing the right thing.

---

### Post by Klonoa on 2008-03-31
Now it doesnt do it on log out or log in anymore, now it just does it in some windows when the close and stuff (after I click close). And sometimes windows just appear with them, like i was printing something and the display window was covered with them. And I;m using the default graphics controller that came with the computer, it has never done this before. Which Xorg theres 2 and a .old one.

---

### Post by Klonoa on 2008-04-01
> 
(process:5169): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5173): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
SESSION_MANAGER=local/kaze-desktop:/tmp/.ICE-unix/5166
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:01.0 0300: 8086:7125 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Initializing gnome-mount extension
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Initializing nautilus-open-terminal extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
applet.py: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gtk-window-decorator' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'bluetooth-applet' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
update-notifier: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-volume-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
metacity: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nm-applet: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
restricted-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
evolution-alarm-notify: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
vino-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
That is my errors log for xsession, just to let you know and i accidentally moved a copy of it to my desktop can you help me delete it?

---

