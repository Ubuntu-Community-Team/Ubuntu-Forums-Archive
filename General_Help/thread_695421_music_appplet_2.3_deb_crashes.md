---
title: "music appplet 2.3 deb crashes"
date: 2008-02-13
forum: General Help
---

### Post by zeltak on 2008-02-13
Hi all

Ive installed the new deb file from get deb  music applet 2.30 on gutsy 64 bit system. The applet wont even load and crashes all the time. When i try to load it from the CLI i get this:

DEBUG: GConf root is /apps/panel/applets/applet_17/prefs
Failed to open module at /usr/share/python-support/music-applet/musicapplet/plugins/__init__.py: 'module' object has no attribute 'INFO'
Failed to scan /home/zeltak/.gnome2/music-applet/plugins: [Errno 2] No such file or directory: '/home/zeltak/.gnome2/music-applet/plugins'
music-applet: Unknown option '--oaf-activate-iid=OAFIID:GNOME_Music_Applet_Factory'.
music-applet: Use --help to get a list of available command line options.

** (music-applet:29663): WARNING **: FIXME: wait for completion unimplemented

Does any one know how to solve this?

thx

Zeltak

---

### Post by zeltak on 2008-02-17
ok some progress but no solution

I uninstalled everything (my previous attempts to build from source, deb files etc..) and tried to install the deb file

If i manually launch "/usr/lib/gnome-applets/music-applet" i can then add the panel applet manually to the panel and it Works!!:confused:....

But...after a restart/login it crashes again....

this is the output i get when launching manaully

~$ /usr/lib/gnome-applets/music-applet
DEBUG: GConf root is /apps/panel/applets/applet_19/prefs
Failed to open module at /usr/share/python-support/music-applet/musicapplet/plugins/__init__.py: 'module' object has no attribute 'INFO'
Failed to scan /home/zeltak/.gnome2/music-applet/plugins: [Errno 2] No such file or directory: '/home/zeltak/.gnome2/music-applet/plugins'
QApplication: There should be max one application object


Can anyone help?

thx

Zeltak

---

### Post by meindian523 on 2008-02-17
> **zeltak said:**
> 
~$ /usr/lib/gnome-applets/music-applet
DEBUG: GConf root is /apps/panel/applets/applet_19/prefs

Try checking whether the root IS in /apps/panel/applets/applet_19/prefs.To do that,enter ```
gconf-editor
``` in terminal and verify.

> **zeltak said:**
> 
Failed to open module at /usr/share/python-support/music-applet/musicapplet/plugins/__init__.py: 'module' object has no attribute 'INFO'
Failed to scan /home/zeltak/.gnome2/music-applet/plugins: [Errno 2] No such file or directory: '/home/zeltak/.gnome2/music-applet/plugins'
QApplication: There should be max one application object


Try creating a .gnome2/music-applet/plugins folder inside your home folder.

---

### Post by zeltak on 2008-02-17
thx for the answer!

I did the 2nd step (create missing folders), but i couldnt understand the first part.

I launced the gconf editor and searched  in
/apps/panel/applets/applet_19/prefs

But i cant see a Root entry...should i create one? is so how do i do it?

thx

Zeltak

---

### Post by meindian523 on 2008-02-17
Could you post ```
music-applet --help
```?

---

### Post by zeltak on 2008-02-17
this is what i get when i paste music-applet --help in the terminal

zeltak@voices:~$ music-applet --help
bash: music-applet: command not found


Its strange since if i run 
/usr/lib/gnome-applets/music-applet

it loads the applet to the add applet menu

Zeltak

---

### Post by meindian523 on 2008-02-17
Try doing /usr/lib/gnome-applets/music-applet --help then.

---

### Post by zeltak on 2008-02-17
Hi

here is the output

/usr/lib/gnome-applets/music-applet --help
Usage: music-applet [OPTION...]
  --load-modules=MODULE1,MODULE2,...     Dynamic modules to load

Help options
  -?, --help                             Show this help message
  --usage                                Display brief usage message

GTK+
  --gdk-debug=FLAGS                      Gdk debugging flags to set
  --gdk-no-debug=FLAGS                   Gdk debugging flags to unset
  --display=DISPLAY                      X display to use
  --screen=SCREEN                        X screen to use
  --sync                                 Make X calls synchronous
  --name=NAME                            Program name as used by the window
                                         manager
  --class=CLASS                          Program class as used by the window
                                         manager
  --gtk-debug=FLAGS                      Gtk+ debugging flags to set
  --gtk-no-debug=FLAGS                   Gtk+ debugging flags to unset
  --g-fatal-warnings                     Make all warnings fatal
  --gtk-module=MODULE                    Load an additional Gtk module

Bonobo activation Support
  --oaf-ior-fd=FD                        File descriptor to print IOR on
  --oaf-activate-iid=IID                 IID to activate
  --oaf-private                          Prevent registering of server with OAF

GNOME Library
  --disable-sound                        Disable sound server usage
  --enable-sound                         Enable sound server usage
  --espeaker=HOSTNAME:PORT               Host:port on which the sound server
                                         to use is running
  --version                              2.20.0

Session management
  --sm-client-id=ID                      Specify session management ID
  --sm-config-prefix=PREFIX              Specify prefix of saved configuration
  --sm-disable                           Disable connection to session manager

GNOME GUI Library
  --disable-crash-dialog                 Disable Crash Dialog


thx again

Zeltak

---

### Post by meindian523 on 2008-02-17
Um,that's no a helpful help. :(
Could you post what are the keys in /apps/panel/applets/applet_19/prefs

---

### Post by zeltak on 2008-03-06
Hi again

I think i finally now whats going on. It seems that i compiled the 2.3 version a while ago and its still on my system even i after i use synaptic to uninstall. I dont have the original folder with the make file i used to install music applet. I think thats why the deb file keeps crashing. Does anyone know how to manually remove all previous music applet entries?

thx

Zeltak

---

