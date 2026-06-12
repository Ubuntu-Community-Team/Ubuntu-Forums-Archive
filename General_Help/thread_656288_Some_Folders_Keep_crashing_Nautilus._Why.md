---
title: "Some Folders Keep crashing Nautilus. Why?"
date: 2008-01-02
forum: General Help
---

### Post by DAE_JA_VOO on 2008-01-02
Hi guys

For some reason, Nautilus becomes unresponsive when i try to open some folders. Not ALL folders, but some. My "Pictures" folder is one such folder. Even if i just single click on it, Nautilus turns grey and i need to Force Quit it.

Any ideas?

---

### Post by chrisccoulson on 2008-01-02
Do the folders contain a large number of files? Have you tried disabling thumbnails in Nautilus preferences, to see if the problem goes away?

---

### Post by DAE_JA_VOO on 2008-01-02
> **chrisccoulson said:**
> Do the folders contain a large number of files? Have you tried disabling thumbnails in Nautilus preferences, to see if the problem goes away?

Thanks for the reply :)

Yes, the folders do contain quite a lot of Data, be it files in that folder, or files within folders within THAT folder.

Disabling Thumbnails didn't help :(

Let me just mention that i haven't had this problem before. These folders have not increased in size dramatically over the last while...

---

### Post by chrisccoulson on 2008-01-02
Does it happen with all users, or just the one user? If it's specifiic to your profile, you could try resetting your Nautilus profile and see if that helps:
```
mv ~/.nautilus ~/.nautilus_old
killall nautilus
```

The first line resets your Nautilus profile but will enable you to restore the settings if you need to. The second line should restart Nautilus

---

### Post by DAE_JA_VOO on 2008-01-02
Hey Chris

I've tried on both MY user and the admin user, the problem seems to be the same. 

Nautilus doesn't ALWAYS freeze... at times it just takes really long to open the folder...

---

### Post by chrisccoulson on 2008-01-02
Is anything being logged in your ~/.xsession-errors file? Could you try it with a fresh profile? Have you got any debug logs in your home folder (nautilus-debug-log.txt)?

---

### Post by DAE_JA_VOO on 2008-01-02
Hi Chris

Here's my xsession-errors file:

> (process:8512): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:8516): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ett-desktop:/tmp/.ICE-unix/8509
Initializing nautilus-open-terminal extension
Checking for Xgl: not present. 
Initializing gnome-mount extension
Detected PCI ID for VGA: 01:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 20462 1199318400 1199297938
evolution-alarm-notify-Message:  Thu Jan  3 02:00:00 2008

evolution-alarm-notify-Message:  Wed Jan  2 20:18:58 2008

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

** (nautilus:8564): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8564): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8564): WARNING **: Can not get _NET_WORKAREA

** (nautilus:8564): WARNING **: Can not determine workarea, guessing at layout
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/gedit.desktop
LOADED : /usr/share/applications/filezilla.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/virtualbox.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sArchiving' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sExecute' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sFile%20Info' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sFile%20Processing' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sFile%20System%20Management' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sMultimedia' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sObsolete' to action group 'ScriptsGroup'
sys:1: GtkWarning: Refusing to add non-unique action 'submenu_file:\s\s\shome\sett\s.gnome2\snautilus-scripts\snautilus-scripts\sSystem%20Configuration' to action group 'ScriptsGroup'
/usr/share/envy/gtkenvy.py:58: GtkWarning: Ignoring the separator setting
  self.wTree = gtk.glade.XML(self.gladefile)

(gtkenvy.py:8769): libglade-WARNING **: could not find a parent that handles internal children for `vbox'

(gtkenvy.py:8769): libglade-WARNING **: could not find a parent that handles internal children for `vbox'

(gtkenvy.py:8769): libglade-WARNING **: could not find a parent that handles internal children for `vbox'

(gtkenvy.py:8769): libglade-WARNING **: could not find a parent that handles internal children for `vbox'

(gtkenvy.py:8769): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
Launched application : 8777
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
GMarks - notes error
URIError: malformed URI sequence
GMarks - notes error
URIError: malformed URI sequence
Launched application : 9047
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

	 You will not be able to start VMs until this problem is fixed.
Launched application : 9140
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

	 You will not be able to start VMs until this problem is fixed.
checking for ubuntu...
found and fixing ubuntu
checking for ubuntu...
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.

Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentCreator
Initialising plugin WebUi
Initialising plugin BlocklistImport
Initialising plugin NetworkHealth
Initialising plugin SpeedLimiter
Initialising plugin ExtraStats
Initialising plugin TorrentNotification
Initialising plugin TorrentFiles
Initialising plugin EventLogging
Initialising plugin NetworkGraph
Initialising plugin FlexRSS
Initialising plugin Scheduler
Initialising plugin MoveTorrent
Initialising plugin DesiredRatio
Initialising plugin TorrentPeers
Initialising plugin WebSeed
Applying preferences
Starting DHT...
Showing window
Pickling state...
Loading TorrentFiles plugin...
Loading TorrentPeers plugin...
Pickling state...
Raising error: Handle not found.

Pickling state...
Raising error: Handle not found.

Pickling state...
Stopping DHT...
Saving fastresume data...
Saving uploaded memory...
Quitting the core...
core: removing torrents...

core: removing settings...

core: shutting down session...

core shut down.

Conky: forked to background, pid is 9220

Conky: desktop window (c000af) is subwindow of root window (1a5)
Conky: window type - normal
Conky: drawing to created window (3200001)
Conky: drawing to double buffer
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory
python: can't open file '/home/ett/.scripts/gmail.py': [Errno 2] No such file or directory

Ther eare no debugs in the nautilus file, unfortunately :(

I created a new user and tried but i had the same problems :(

---

### Post by DAE_JA_VOO on 2008-01-03
Bump

---

### Post by DAE_JA_VOO on 2008-01-06
Bump

---

### Post by oldos2er on 2008-01-06
Have you run fsck lately?

---

### Post by DAE_JA_VOO on 2008-01-12
fsck? I don't even know what that is :(

---

### Post by Sidewinder1 on 2008-01-12
fsck is (I believe)  for file system check, run from the command line. There should be a "man" page. BTW sometimes, when I boot I get a black screen (prior to log in) saying something to the effect: "system has been mounted 38 times without fsck. It will be forced." Then it proceeds to go through the percentage "run-up" 'til it's finished; then the system boots normally. If I am incorrect in any of the above, perhaps someone more knolegable than I can enlighten you. I'm such a noob.
:-)   HTH,

---

### Post by chrisccoulson on 2008-01-12
Yes, fsck is indeed a file system checker (well, technically, it is just a wrapper for fsck.ext3, fsck.vfat etc...)

Whatever you do, **[SIZE="4"]never run fsck on a mounted filesystem[/SIZE]**, else you will risk data loss

---

### Post by Sidewinder1 on 2008-01-12
Chris, Thank you ever so much for that warning; I never knew that. Can't tell you how much grief you probably saved me and hopefully others. Now, if I can only remember it 3 wks. from now.

---

### Post by kared on 2008-07-08
For me it helped to disable the thumbnails. It seems that my .tif files caused nautilus to chew for quite a while, even if there was only one or a few in the directory.
Kare

---

