---
title: "gedit: file saving is still disabled"
date: 2013-03-16
forum: General Help
---

### Post by nmmarkin on 2013-03-16
I have exact the same problem like in this thread [http://ubuntuforums.org/showthread.php?t=1483902&page=3](http://ubuntuforums.org/showthread.php?t=1483902&page=3) but, unfortunately to me, for some strange reasons the solution doesn't work for me. Is there yet any thoughts what could be done to fix it?

Here are some key moments of the problem:
[LIST]
[*]gedit doesn't allow me to save any file even a new one
[*]it shows me an alert with the message "saving has been disabled by system administrator" on exit
[*]other editors don't have problems with a file saving and work predictable
[*]other account also doesn't meet any difficulties with a file saving
[*]under root user gedit works fine (no wonder)
[*]the flag /desktop/gnome/lockdown/disable_save_to_disk in the configure editor gconf-editor is cleared
[/LIST]

[SIZE=1]Ubuntu 12.10[/SIZE]

---

### Post by stinkeye on 2013-03-16
Depending on your release it may be in dconf-editor
Check this section...
org.gnome.desktop.lockdown

Check via terminal
```
gsettings **get** org.gnome.desktop.lockdown disable-save-to-disk
```

If true reset to false(default)
```
gsettings **reset** org.gnome.desktop.lockdown disable-save-to-disk
```


...and check again with first command.

---

### Post by nmmarkin on 2013-03-16
thank you so much!

---

