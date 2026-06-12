---
title: "Dropbox not working.  How to debug and fix?"
date: 2024-07-21
forum: General Help
---

### Post by Tom_Carr on 2024-07-21
I am running ubuntu jammy.  I installed dropbox right after installing ubuntu jammy, and dropbox worked fine.  I just checked though, and it has not updated any files since 1/4/24.  I checked the online site.  I have only been using on one desktop in the last year.  Nothing else linked with dropbox.

How do I debug this?  Or should I just uninstall and reinstall?

If uninstalling and reinstalling.  How do I do this?  I am a light weight low tech user, so please answer as simply as possible.

---

### Post by currentshaft on 2024-07-22
How did you install Dropbox? Apt? Flatpak? Snap?

sudo apt update && sudo apt upgrade
flatpak update
sudo snap refresh

Then does the application start?

---

### Post by Tom_Carr on 2024-07-24
I installed dropbox by going to the "ubuntu software" icon.  Did a search and found the dropbox app and hit the install button.

I rarely use the terminal if I can do things with the GUI.

---

### Post by currentshaft on 2024-07-24
Using the terminal in Ubuntu is like owning a toolbox as a homeowner. The more you are comfortable with it, the easier your life will be.

The commands I gave you to run are safe and just check for and install any pending updates.

---

### Post by Tom_Carr on 2024-07-26
I pasted the commands you gave me into the terminal and this is what I got:

tom@tom-OptiPlex-3040:~$ ^[[200~sudo apt update && sudo apt upgrade
sudo: command not found
tom@tom-OptiPlex-3040:~$ flatpak update
flatpak: command not found
tom@tom-OptiPlex-3040:~$ sudo snap refresh
[sudo] password for tom: 
Sorry, try again.
[sudo] password for tom: 
firefox 128.0.3-1 from Mozilla&#10003; refreshed
tom@tom-OptiPlex-3040:~$

---

### Post by Tom_Carr on 2024-07-26
How do I know if it is running?  I went to the dropbox web site and I don't see anything getting updated.

---

### Post by #&amp;thj^% on 2024-07-26
We are still trying to figure out what type dropbox you have.
```
apt policy dropbox
```
and
```
snap list
```
and 
```
flatpak list
```
When we see those we might be able to give you safe advise.

---

### Post by deadflowr on 2024-07-26
It can only be a deb.
No dropbox snap packages, and the user would have to add flatpak manually.

---

### Post by #&amp;thj^% on 2024-07-26
> **deadflowr said:**
> It can only be a deb.
No dropbox snap packages, 

I don't do snaps so I wouldn't of known that, but i do now. ;)
```
apt policy dropbox 
dropbox:
  Installed: 2024.04.17
  Candidate: 2024.04.17
  Version table:
 *** 2024.04.17 100
        100 /var/lib/dpkg/status

```
>  How do I know if it is running? I went to the dropbox web site and I don't see anything getting updated. 
Like this:
```
dropbox running

```
Or
```
dropbox start 
Dropbox is already running!

```
Just show us that then. Or not....lol
```
Dropbox command-line interface

commands:

Note: use dropbox help <command> to view usage for a specific command.

 autostart    automatically start Dropbox at login
 exclude      ignores/excludes a directory from syncing
 filestatus   get current sync status of one or more files
 help         provide help
 lansync      enables or disables LAN sync
 ls           list directory contents with current sync status
 proxy        set proxy settings for Dropbox
 running      return whether Dropbox is running
 sharelink    get a shared link for a file in your Dropbox
 start        start dropboxd
 status       get current status of the dropboxd
 stop         stop dropboxd
 throttle     set bandwidth limits for Dropbox
 update       download latest version of Dropbox
 version      print version information for Dropbox
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```

---

### Post by Tom_Carr on 2024-07-27
I'll do everything requested in terminal and post the results here


tom@tom-OptiPlex-3040:~$ apt policy dropbox
dropbox:
  Installed: (none)
  Candidate: (none)
  Version table:
tom@tom-OptiPlex-3040:~$ snap list
Name                            Version                     Rev    Tracking         Publisher       Notes
bare                            1.0                         5      latest/stable    canonical&#10003;      base
chatgpt-desktop                 1.0.6                       7      latest/stable    joshua-redmond  -
chromium                        126.0.6478.182              2910   latest/stable    canonical&#10003;      -
core18                          20240612                    2829   latest/stable    canonical&#10003;      base
core20                          20240416                    2318   latest/stable    canonical&#10003;      base
core22                          20240408                    1380   latest/stable    canonical&#10003;      base
core24                          20240528                    423    latest/stable    canonical&#10003;      base
cups                            2.4.10-1                    1058   latest/stable    openprinting&#10003;   -
firefox                         128.0.3-1                   4650   latest/stable/&#8230;  mozilla&#10003;        -
gnome-3-28-1804                 3.28.0-19-g98f9e67.98f9e67  198    latest/stable    canonical&#10003;      -
gnome-3-38-2004                 0+git.efb213a               143    latest/stable/&#8230;  canonical&#10003;      -
gnome-42-2204                   0+git.510a601               176    latest/stable    canonical&#10003;      -
gnome-46-2404                   0+git.1f00542               42     latest/stable    canonical&#10003;      -
gtk-common-themes               0.1-81-g442e511             1535   latest/stable/&#8230;  canonical&#10003;      -
hunspell-dictionaries-1-7-2004  1.7-20.04+pkg-6fd6          2      latest/stable    brlin           -
kf5-5-110-qt-5-15-11-core22     5.110                       3      latest/stable    kde&#10003;            -
konqueror                       23.08.4                     35     latest/stable    kde&#10003;            -
mesa-2404                       24.0.5                      44     latest/stable    canonical&#10003;      -
skype                           8.124.0.204                 351    latest/stable    skype&#10003;          -
snap-store                      41.3-77-g7dc86c8            1113   latest/stable/&#8230;  canonical&#10003;      -
snapd                           2.63                        21759  latest/stable    canonical&#10003;      snapd
snapd-desktop-integration       0.9                         157    latest/stable/&#8230;  canonical&#10003;      -
vlc                             3.0.20-1-g2617de71b6        3777   latest/stable    videolan&#10003;       -
zoom-client                     6.0.12.5501                 230    latest/stable    ogra            -
tom@tom-OptiPlex-3040:~$ flatpak list
flatpak: command not found
tom@tom-OptiPlex-3040:~$

---

### Post by Tom_Carr on 2024-07-27
tom@tom-OptiPlex-3040:~$ dropbox running
tom@tom-OptiPlex-3040:~$ dropbox start
Starting Dropbox...dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/apex._apex.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtCore.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.sip.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtGui.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtWidgets.so'
Dropbox isn't running!
Done!
tom@tom-OptiPlex-3040:~$ dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtDBus.so'


(dropbox:55753): LIBDBUSMENU-GLIB-WARNING **: 18:01:28.669: About to Show called on an item wihtout submenus.  We're ignoring it.
^C
tom@tom-OptiPlex-3040:~$

---

### Post by #&amp;thj^% on 2024-07-27
You don't even have it installed, please do so here: [https://www.dropbox.com/install-linux](https://www.dropbox.com/install-linux)
You will want this one "Ubuntu 22.10 or higher (.deb)	 	64-bit" download and install it.

---

### Post by #&amp;thj^% on 2024-07-27
> **Tom_Carr said:**
> tom@tom-OptiPlex-3040:~$ dropbox running
tom@tom-OptiPlex-3040:~$ dropbox start
Starting Dropbox...dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/apex._apex.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtCore.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.sip.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtGui.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtWidgets.so'
Dropbox isn't running!
Done!
tom@tom-OptiPlex-3040:~$ dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/PyQt5.QtDBus.so'


(dropbox:55753): LIBDBUSMENU-GLIB-WARNING **: 18:01:28.669: About to Show called on an item wihtout submenus.  We're ignoring it.
^C
tom@tom-OptiPlex-3040:~$
Ok it's not finished installed, please run:
```
dropbox -i
```

---

### Post by dragonfly41 on 2024-07-28
> [COLOR=#000000] I am a light weight low tech user, so please answer as simply as possible.
I look at desktop top left bar .. Activities ... type: dropbox.
I see Dropbox launcher.
Click to start.[/COLOR]

---

### Post by Tom_Carr on 2024-07-30
> [COLOR=#000000]I look at desktop top left bar .. Activities ... type: dropbox.[/COLOR]
[COLOR=#000000]I see Dropbox launcher.[/COLOR]
[COLOR=#000000]Click to start.[/COLOR]

I went there and it said it was installed.

Should I go to the terminal and enter  

> dropbox -i

I don't know how it could be only partially installed or not installed at all.  I have been using it since mid 2022.  It was working fine.  I don't check it that often, but when I checked last week it had not updated anything since 1/4/2024

---

### Post by #&amp;thj^% on 2024-07-30
Or just to see, run both:
```
dropbx -i
## And
dropbox update
```

---

### Post by deadflowr on 2024-07-30
Dropbox is the nautilus-dropbox package in Ubuntu.
It's actually one of those oddball packages much like the old flashplugin package, where the package just runs an installer script that downloads and installs the closed-source binary.
Also adds some integration into Files (nautilus) so you can access the files through the file manager instead of some app.

With nothing to go but a brief look at their own troubleshooting on this issue, what is the current firewall status on the desktop?

---

### Post by Tom_Carr on 2024-07-30
I did this:

> dropbx -i
## And
dropbox update

And got a message saying "download binary does not match dropbox signature, aborting install.

---

### Post by #&amp;thj^% on 2024-07-30
Well did it start? please include a little more info in your replys
```
dropbox start

```
This is normal if it is up to date
> **Tom_Carr said:**
> 
And got a message saying "download binary does not match dropbox signature, aborting install.
```
 dropbox version
Dropbox daemon version: 204.4.5420
Dropbox command-line interface version: 2019.02.14

```

---

### Post by Tom_Carr on 2024-07-30
tom@tom-OptiPlex-3040:~$ dropbx -i
## And
dropbox update
Command 'dropbx' not found, did you mean:
  command 'dropbox' from deb nautilus-dropbox (2019.02.14-1ubuntu1)
Try: sudo apt install <deb name>
/usr/bin/dropbox:303: PyGIDeprecationWarning: Since version 3.11, calling threads_init is no longer needed. See: [https://wiki.gnome.org/PyGObject/Threading](https://wiki.gnome.org/PyGObject/Threading)
  GObject.threads_init()
/usr/bin/dropbox:453: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  self.ok = ok = Gtk.Button(stock=Gtk.STOCK_OK)
/usr/bin/dropbox:458: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  cancel = Gtk.Button(stock=Gtk.STOCK_CANCEL)
/usr/bin/dropbox:348: DeprecationWarning: setDaemon() is deprecated, set the daemon attribute instead
  t.setDaemon(True)
/usr/bin/dropbox:334: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.loop_callback, *ret)
/usr/bin/dropbox:344: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.on_done)
/usr/bin/dropbox:348: DeprecationWarning: setDaemon() is deprecated, set the daemon attribute instead
  t.setDaemon(True)


/usr/bin/dropbox:341: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.on_exception, e)
/usr/bin/dropbox:309: PyGTKDeprecationWarning: The keyword(s) "type, message_format" have been deprecated in favor of "message_type, text" respectively. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  error = Gtk.MessageDialog(parent = None,
/usr/bin/dropbox:309: PyGTKDeprecationWarning: The "flags" argument for dialog construction is deprecated. Please use initializer keywords: modal=True and/or destroy_with_parent=True. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  error = Gtk.MessageDialog(parent = None,

---

### Post by Tom_Carr on 2024-07-30
> [COLOR=#000000]Well did it start? please include a little more info in your replys[/COLOR]

Will do.  Thanks for your continued help and patience.[COLOR=#000000][/COLOR]

---

### Post by #&amp;thj^% on 2024-07-30
This is a typeO on my side, sorry.
it is:
```
 dropbox -i
```
If you would, show me both of these
and
```
dropbox update
```
Now this one I would really like to see:
```
dropbox start
```

---

### Post by Tom_Carr on 2024-07-30
tom@tom-OptiPlex-3040:~$ dropbox -i
Dropbox command-line interface


commands:


Note: use dropbox help <command> to view usage for a specific command.


 autostart    automatically start Dropbox at login
 exclude      ignores/excludes a directory from syncing
 filestatus   get current sync status of one or more files
 help         provide help
 lansync      enables or disables LAN sync
 ls           list directory contents with current sync status
 proxy        set proxy settings for Dropbox
 puburl       get public url of a file in your Dropbox's public folder
 running      return whether Dropbox is running
 sharelink    get a shared link for a file in your Dropbox
 start        start dropboxd
 status       get current status of the dropboxd
 stop         stop dropboxd
 throttle     set bandwidth limits for Dropbox
 update       download latest version of dropbox
 version      print version information for Dropbox
tom@tom-OptiPlex-3040:~$ dropbox update
/usr/bin/dropbox:303: PyGIDeprecationWarning: Since version 3.11, calling threads_init is no longer needed. See: [https://wiki.gnome.org/PyGObject/Threading](https://wiki.gnome.org/PyGObject/Threading)
  GObject.threads_init()
/usr/bin/dropbox:453: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  self.ok = ok = Gtk.Button(stock=Gtk.STOCK_OK)
/usr/bin/dropbox:458: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  cancel = Gtk.Button(stock=Gtk.STOCK_CANCEL)
/usr/bin/dropbox:348: DeprecationWarning: setDaemon() is deprecated, set the daemon attribute instead
  t.setDaemon(True)
/usr/bin/dropbox:334: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.loop_callback, *ret)
/usr/bin/dropbox:344: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.on_done)
/usr/bin/dropbox:348: DeprecationWarning: setDaemon() is deprecated, set the daemon attribute instead
  t.setDaemon(True)
/usr/bin/dropbox:334: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.loop_callback, *ret)
/usr/bin/dropbox:344: PyGIDeprecationWarning: GObject.idle_add is deprecated; use GLib.idle_add instead
  GObject.idle_add(self.on_done)
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/apex._apex.abi3.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/tom/.dropbox-dist/dropbox-lnx.x86_64-204.4.5420/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
success!
tom@tom-OptiPlex-3040:~$ dropbox start
/usr/bin/dropbox:613: DeprecationWarning: isSet() is deprecated, use is_set() instead
  if self.stop_event.isSet(): break
Dropbox is already running!
tom@tom-OptiPlex-3040:~$

---

### Post by #&amp;thj^% on 2024-07-31
Looks to me like it is running via:
```
tom@tom-OptiPlex-3040:~$ dropbox start
/usr/bin/dropbox:613: DeprecationWarning: isSet() is deprecated, use is_set() instead
if self.stop_event.isSet(): break
Dropbox is already running!
```
```
 dropbox version
Dropbox daemon version: 204.4.5420
Dropbox command-line interface version: 2019.02.14

```

Is this now Solved?

---

### Post by Tom_Carr on 2024-07-31
It is not updating the files in the dropbox folder online.  So it is not working even if it is running.

---

### Post by #&amp;thj^% on 2024-07-31
> **Tom_Carr said:**
> It is not updating the files in the dropbox folder online.  So it is not working even if it is running.

That is good info, and to try and shorten our reply's please see this: [https://help.dropbox.com/sync/files-not-syncing](https://help.dropbox.com/sync/files-not-syncing)

You should go down the list on that page to ensure a good outcome.

Good Luck

---

### Post by Tom_Carr on 2024-07-31
> [COLOR=#000000][INDENT]That is good info, and to try and shorten our reply's please see this: [https://help.dropbox.com/sync/files-not-syncing](https://help.dropbox.com/sync/files-not-syncing)

You should go down the list on that page to ensure a good outcome.

Good Luck[/INDENT]
[/COLOR]
[INDENT]Will do.  Will dig into that tomorrow if time permits.  Thanks for all your help on this.  I will leave the thread open for now just in case I get stuck.  Thanks again.[/INDENT]

---

### Post by Tom_Carr on 2024-08-18
I have been very busy with no time to work on this.  Now I have free time.

I went to the link suggested: [COLOR=#000000]* *[/COLOR][https://help.dropbox.com/sync/files-not-syncing](https://help.dropbox.com/sync/files-not-syncing)

The first thing it recommends is "Check your firewall, security, and antivirus settings".   I have just used the settings that came when I originally set up ubuntu.  I have never looked at then or changed them.  Is it important to dig into this?

The next thing is to back up everything very carefully, then uninstall and reinstall dropbox.

I am only using dropbox on one computer to back up changes.

---

