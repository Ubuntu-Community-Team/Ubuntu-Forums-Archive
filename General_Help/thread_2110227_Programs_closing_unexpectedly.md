---
title: "Programs closing unexpectedly"
date: 2013-01-29
forum: General Help
---

### Post by e_torano on 2013-01-29
I'm running Ubuntu 12.10 and have been doing so since I fresh installed it as an upgrade from 12.04 on release day. Everything's been fairly smooth (if slow) up till about a week ago. Now, just about every program I try to open closes unexpectedly. Chromium and Sublime Text 2 are just about the only programs that are working reliably at this point. Even the report problem dialogue hangs up whilst trying to retrieve the debug details to send an error report.

I've tried starting programs via the Terminal with no more luck too. here's what happened when I tried running gnome-tweak-tool:

```
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key repeat)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click-volume)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-mode)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-pitch)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-duration)
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 172, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 164, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 47, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 58, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 147, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 209, in <module>
    class StaticWorkspaceTweak(Tweak):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 214, in StaticWorkspaceTweak
    _shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 164, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 47, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files

```

And here's what happens when I try opening Ubuntu Tweak via the terminal:

```
euan@euan-HP-G62-Notebook-PC:~$ ubuntu-tweak
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity

(ubuntu-tweak:5937): Gtk-ERROR **: GtkBox child GtkTreeView minimum width: -1 < 0 for height 335
Trace/breakpoint trap (core dumped)

```

Here's a screenshot of what actually pops up visually too:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230822&stc=1&d=1359493132[/IMG]



Obviously, this is getting to be rather annoying and I'm now on the verge of going for a fresh install (which I'd rather not do right now - 13.04 isn't too far away and I was hoping to last until then). If anybody could shed any kind of insight, I'd be supremely grateful.

Euan

---

### Post by e_torano on 2013-01-29
Also, a potentially separate problem is that all menus have become extremely ugly too:

[https://dl.dropbox.com/s/h9zzh8ka4xfcwyd/IMAG0050.jpg?dl=1](https://dl.dropbox.com/s/h9zzh8ka4xfcwyd/IMAG0050.jpg?dl=1)

Notification bubbles are also completely ugly.

---

### Post by bogan on 2013-01-30
Hi!,** e_torano,**

I had a similar shoal of 'xxxx closed unexpectedly' messages, the other day, including a crash of Apport, the producer of these messages.

However some of mine were real crashes - Update Manager, Synaptic and Apt, amongst them.

I did not get the same Error messages as you, and it was cleared up by running: ```
sudo apt-get update
sudo apt-get -f install --fix-broken
dpkg-reconfigure -a # This may take a long time, wait it out
```You could try the same commands.

I also ran:```
sudo apt-get install --reinstall update-manager
``` As that seemed to be the main culprit.

This followed by a cold restart put things back [Edit] as they were before. Update 48Hrs later, still OK!

Chao!, **bogan.**

---

### Post by e_torano on 2013-01-30
Thanks bogan, I'll run your suggestions and see what happens. Hopefully it may help a bit. Apport always crashes for myself too. I haven't been able to view  full bug report or anything for well over a week.

---

