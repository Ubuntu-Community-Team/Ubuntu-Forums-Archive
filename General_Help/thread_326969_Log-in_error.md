---
title: "Log-in error"
date: 2006-12-28
forum: General Help
---

### Post by Nirva on 2006-12-28
Hi,

I have a little problem with logging in.  I am running Compiz and XGl, and the problem started occuring since I installed those two.
When I log in, I have like 50% chance to get the error.  So sometimes I have to try 5 times before I get logged in, other times, i manage to log in from the first time.
The error is a little message that tells me, that my X-session was shorter then 10 seconds and it tells me I should have a look at my /.xsession-errors.
Because I don't see the problem I will paste it here.  

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "filip"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/Filip:/tmp/.ICE-unix/5838
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:5916): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-panel:5916): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-session:5838): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-session:5838): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field

evolution-alarm-notify-Message: Setting timeout for 20096 1167346800 1167326704
evolution-alarm-notify-Message:  Fri Dec 29 00:00:00 2006

evolution-alarm-notify-Message:  Thu Dec 28 18:25:04 2006


(gnome-power-manager:5982): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-power-manager:5982): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(nautilus:5918): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(nautilus:5918): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field

xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212

(update-notifier:5936): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(update-notifier:5936): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(thunar:6123): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(thunar:6123): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-screensaver:6151): gnome-screensaver-WARNING **: screensaver already running in this session

(gnome-terminal:6155): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6155): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(thunar:6178): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(thunar:6178): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field

totem-video-thumbnailer couln't open file 'file:///media/windows/Documents%20and%20Settings/Filip%20Deleersnijder/NTUSER.DAT'
Reason: Could not determine type of stream..

(thunar:6178): Gtk-WARNING **: Error loading theme icon for stock: Icon 'Terminal' not present in theme

(thunar:6178): Gtk-WARNING **: Error loading theme icon for stock: Icon 'Terminal' not present in theme
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.
** Message: Hit unexpected error "Not on the same file system" while doing a file operation.

(yelp:6317): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(yelp:6317): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-terminal:6382): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6382): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gedit:6398): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gedit:6398): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


Making sure Thunar is installed

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [1220kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [6132B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [365kB]

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  Sub-process gzip returned an error code (1)

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
  Sub-process gzip returned an error code (1)

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
  Sub-process gzip returned an error code (1)
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [4655kB]

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1441kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [162kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [55.3kB]

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
  Sub-process gzip returned an error code (1)

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
  Sub-process gzip returned an error code (1)

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:12 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Fetched 12B in 5s (2B/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information...

Downloading new .desktop files

--18:31:00--  [http://www.psychocats.net/ubuntu/defaultthunar/nautilus-computer.desktop](http://www.psychocats.net/ubuntu/defaultthunar/nautilus-computer.desktop)
           => `nautilus-computer.desktop'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,239 (2.2K) [text/plain]

    0K ..                                                    100%    1.11 MB/s

18:31:00 (1.11 MB/s) - `nautilus-computer.desktop' saved [2239/2239]

--18:31:00--  [http://www.psychocats.net/ubuntu/defaultthunar/nautilus.desktop](http://www.psychocats.net/ubuntu/defaultthunar/nautilus.desktop)
           => `nautilus.desktop'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,384 (7.2K) [text/plain]

    0K .......                                               100%   74.25 KB/s

18:31:01 (74.25 KB/s) - `nautilus.desktop' saved [7384/7384]

--18:31:01--  [http://www.psychocats.net/ubuntu/defaultthunar/nautilus-folder-handler.desktop](http://www.psychocats.net/ubuntu/defaultthunar/nautilus-folder-handler.desktop)
           => `nautilus-folder-handler.desktop'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,669 (1.6K) [text/plain]

    0K .                                                     100%    2.93 MB/s

18:31:01 (2.93 MB/s) - `nautilus-folder-handler.desktop' saved [1669/1669]

--18:31:01--  [http://www.psychocats.net/ubuntu/defaultthunar/nautilus-home.desktop](http://www.psychocats.net/ubuntu/defaultthunar/nautilus-home.desktop)
           => `nautilus-home.desktop'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,773 (2.7K) [text/plain]

    0K ..                                                    100%  858.32 KB/s

18:31:02 (858.32 KB/s) - `nautilus-home.desktop' saved [2773/2773]


Making backup copies of old .desktop files


Replacing old .desktop files with new .desktop files


Thunar should now be your new default file manager in Gnome


(file-managment-properties:6610): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(file-managment-properties:6610): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-terminal:6692): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6692): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-terminal:6707): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6707): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(thunar:6760): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(thunar:6760): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-terminal:6771): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6771): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field


(gnome-terminal:6785): Gtk-WARNING **: Theme directory 24x24/apps of theme Gnome-Apple has no size field


(gnome-terminal:6785): Gtk-WARNING **: Theme directory 24x24/stock of theme Gnome-Apple has no size field

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

GCJ PLUGIN: thread 0x81248f0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x81248f0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x81248f0: NP_GetValue
GCJ PLUGIN: thread 0x81248f0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x81248f0: NP_GetValue return
GCJ PLUGIN: thread 0x81248f0: NP_GetValue
GCJ PLUGIN: thread 0x81248f0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x81248f0: NP_GetValue return
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!



Thanks

---

