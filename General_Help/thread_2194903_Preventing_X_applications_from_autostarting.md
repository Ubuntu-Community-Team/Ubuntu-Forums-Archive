---
title: "Preventing X applications from autostarting?"
date: 2013-12-21
forum: General Help
---

### Post by AussieGuy on 2013-12-21
Whenever I reboot, or restart X (with Right Alt, PrtSc, K), I have a whole lot of annoyances which need to be fixed.  An evince window is opened, trying to access a now non-existent file.  Emacs is opened, but in a directory I hardly ever use.  Konsole is started, again in a now unused directory.  Some of the icons in my Panel are in the wrong place.  Somewhere on my system there must be an autostart file telling all this to happen.  However, the following:

~/.kde/Autostart
~/.kde/share/autostart
~/.local/share/autostart

are all empty.  So I've got no idea what file is driving the current autostart behavior, or how to stop it.  I'm using KDE 4.8.5; before that I was using Cinnamon, and before that, Gnome Unity.  Oh, I've also checked Autostart in the "Startup and Shutdown" item of System Settings.  There's nothing there which would drive the behaviour I've described.

Any ideas how to flush out my autostarts, so as to be able to start again, with only the applications I actually want opening?

Thanks,
-A.

---

### Post by ajgreeny on 2013-12-21
Is your session saved from a previous shutdown, and then restarted at next startup?

I have no idea where KDE might save those files but look for hidden files somewhere in your home in a folder called session or similar.

See what help you can get from ```
locate -i session | grep $USER
``` which will list anything in your home with the word **session** in the file or folder name.

---

