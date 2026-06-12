---
title: "Network manager and power manager (battery) do not appear by default on startup"
date: 2014-04-20
forum: General Help
---

### Post by john135 on 2014-04-20
I just upgraded to Xubuntu 14.04 and the first thing I noticed was that the network manager and power manager do not appear by default upon startup. I checked the autostart settings under "Session and Startup" and they are both checked. If I type "sudo nm-applet" and "sudo xfce4-power-manager" both will come up but only for the current session. I'm getting sick of having to type those commands every time I log in. 

Any idea on how to fix this? I'm not sure if this is an issue for all startup features or only these two, but these are the only ones I've noticed missing so far. 

Thanks in advance...

PS: I'm not entirely sure, but I feel like my computer is running a little slower than it did with 13.10.

---

### Post by Toz on 2014-04-20
You shouldn't be starting nm-applet and xfce4-power-manager using sudo. They should be run from userspace (no sudo). I wonder if you're session is saved with these 2 programs as sudo and thus not starting properly on login. Try clearing your sessions cache (Settings Manager -> Session and Startup -> Sessions tab -> "Clear saved sessions"). Log out and back in again to test. They should start automatically.

---

### Post by john135 on 2014-04-20
Unfortunately that doesn't work, I have already tried it :(

---

### Post by Toz on 2014-04-20
Try it the manual way. 
1. First log out. 
2. Then go to the first tty (Ctrl+Alt+F1). 
3. Log in to the text console. 
4. Delete the folder:
```
cd .cache
rm -rf sessions
```
5. Go back to the gui (Ctrl+Alt+F7)
6. Log in and test.

If the two applets don't automatically start, then try starting them manually at the terminal without sudo:
```
nm-applet
```
...and:
```
xfce4-power-manager
```
...and post back any error messages that might come up.

---

### Post by john135 on 2014-04-20
So that took care of the power manager. Now it seems to appear when I log in. However the network manager icon still does not appear.

When I type "nm-applet", nothing really happens, the prompt just disappears and all I see is the blinking cursor (kinda like when you open a window from the terminal without the '&' at the end). If I hit Ctrl+C, the the following message is displayed "^Cnm-applet-Message: PID 0 (we are 2073) sent signal 2, shutting down..."

Additionally, and I don't know if this is of any help, but if I start nm-applet as sudo, the following message appears "nm-applet-Message: using fallback from indicator to GtkStatusIcon"
 and then again the prompt is gone until I hit Ctrl+C or exit the terminal (note: if I hit Ctrl+C, the network tray icon also disappears, so i just exit the terminal)

---

### Post by Toz on 2014-04-20
> When I type "nm-applet", nothing really happens, the prompt just disappears and all I see is the blinking cursor (kinda like when you open a window from the terminal without the '&' at the end). If I hit Ctrl+C, the the following message is displayed "^Cnm-applet-Message: PID 0 (we are 2073) sent signal 2, shutting down..."
Does the network tray icon appear? 
What does the following return:
```
ps -ef | grep nm-applet
```

---

### Post by john135 on 2014-04-20
No it does not appear. 

This is what is returned:
```


*myusername  5100  4887  0 18:51 ?        00:00:00 nm-applet
*myusername  5556  5522  0 18:52 pts/7    00:00:00 grep --color=auto nm-applet


```

---

### Post by Toz on 2014-04-20
Hmmm, nm-applet seems to be running. Try:
```
pkill nm-applet
```
...then
```
nm-applet
```
Does the tray icon appear?

---

### Post by john135 on 2014-04-20
I got an error message:

"** (nm-applet:7232): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-DXCR46or2z: Connection refused"

and the tray icon did not appear....

---

### Post by Toz on 2014-04-20
Is network-manager-gnome installed? 

And what does the following return:
```
sudo service networking status
```

---

### Post by john135 on 2014-04-20
I'm not sure, I assume it is since all I did was upgrade xubuntu. 

Here's what is returned : "networking start/running"

---

### Post by Toz on 2014-04-20
What happens if you change your appearance theme and icon themes? Does the icon then appear?

---

### Post by john135 on 2014-04-20
nope, that doesn't fix it.

---

### Post by Toz on 2014-04-21
What is the height (Row size) of the panel that the icon should appear on? Does changing the size help to bring it back?

Can you try removing the indicator plugin from the panel and then re-adding it?

What does the following return?
```
apt-cache policy network-manager-gnome
```

Can you install the dconf-tools package and the run dconf-editor. Navigate to org->gnome->nm-applet and post back what your settings are?

---

### Post by john135 on 2014-04-22
Sorry for the late response. Classes are killing me. 

No, changing the size of the panel doesn't help (already tried that)

This is what your code returns:
```

network-manager-gnome:
  Installed: 0.9.8.8-0ubuntu4
  Candidate: 0.9.8.8-0ubuntu4
  Version table:
 *** 0.9.8.8-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

I installed dconf-editor and here's what happens: The nm-applet option is checked, however when I uncheck it and check it back, the network icon comes up, however it only stays for a few seconds and then it disappears again. The length of time that it stays up varies. Sometimes is only a couple of seconds, sometimes it's up to a minute lol - That is very weird.

---

### Post by Toz on 2014-04-22
> **john135 said:**
> I installed dconf-editor and here's what happens: The nm-applet option is checked, however when I uncheck it and check it back, the network icon comes up, however it only stays for a few seconds and then it disappears again. The length of time that it stays up varies. Sometimes is only a couple of seconds, sometimes it's up to a minute lol - That is very weird.
Do this again and note what gets logged in ~/.cache/upstart/startxfce4.log. The best way to do this is in an open terminal window, enter:
```
tail -f ~/.cache/upstart/startxfce4.log
```
...then make the change in dconf and note the messages that appear in the log.

---

### Post by john135 on 2014-04-22
the log file appears to be the same before and after I make the change. Nevertheless here's what's in it:

```

thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported input device type.
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::display after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
<Window object at 0x7f693a3b5820 (terminatorlib+window+Window at 0x1c4b030)> is not in registered window list
[2040:2067:0422/230213:ERROR:native_backend_gnome_x.cc(544)] Keyring find failed: 
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
[WARNING:flash/platform/pepper/pep_url_request_info.cpp(219)] Missing colon in HTTP header line "
".
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::display after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::display after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)


** (terminator:2691): WARNING **: Binding '<Shift><Control><Alt>a' failed!
Unable to bind hide_window key, another instance/window has it.
<Window object at 0x7fcb8221a820 (terminatorlib+window+Window at 0x1486030)> is not in registered window list


(xfce4-panel:1508): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:1508): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:1508): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:1508): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed
<Window object at 0x7f0986e75820 (terminatorlib+window+Window at 0x1bf5030)> is not in registered window list


(xfce4-session:1337): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: GNOME compatibility is enabled and gnome-keyring-daemon is found on the system. Skipping gpg/ssh-agent startup.
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-4gEw6C
SSH_AUTH_SOCK=/run/user/1000/keyring-4gEw6C/ssh
GPG_AGENT_INFO=/run/user/1000/keyring-4gEw6C/gpg:0:1


(xfce4-session:3089): xfce4-session-WARNING **: Unable to launch "" (specified by autostart/light-locker.desktop): Text was empty (or contained only whitespace)


** (gnome-sound-applet:3118): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-E44cNbnVDg: Connection refused


** (nm-applet:3124): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-E44cNbnVDg: Connection refused


** (process:3126): CRITICAL **: bluez.vala:104: GDBus.Error:org.bluez.Error.NoSuchAdapter: No such adapter


** (update-notifier:3143): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-E44cNbnVDg: Connection refused


** (polkit-gnome-authentication-agent-1:3152): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-E44cNbnVDg: Connection refused


(zeitgeist-datahub:3161): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(zeitgeist-datahub:3161): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


(polkit-gnome-authentication-agent-1:3152): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed


(polkit-gnome-authentication-agent-1:3152): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (nm-applet:3124): CRITICAL **: nm_secret_agent_register: assertion 'priv->registered == FALSE' failed
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::display after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)
/usr/share/terminator/terminatorlib/terminator.py:87: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  self.gnome_program = gnome.init(APP_NAME, APP_VERSION)


(xfce4-panel:3110): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:3110): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:3110): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(xfce4-panel:3110): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


** (dconf-editor:3363): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-E44cNbnVDg: Connection refused

```

---

### Post by Toz on 2014-04-23
I'm sorry but I'm out of ideas. Might be best to create a bug report for this:
```
ubuntu-bug netowork-manager-gnome
```

---

### Post by john135 on 2014-04-23
Thanks man, you tried hard enough!

---

