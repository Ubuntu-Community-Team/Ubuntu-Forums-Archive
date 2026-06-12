---
title: "Setting default visual effects"
date: 2008-05-23
forum: General Help
---

### Post by revolutio on 2008-05-23
I'd like the visual effects to be set to "None" when I startup Ubuntu instead of the current default of "Normal" which prohibits my watching video (thank you ATI drivers). I do not wish to uninstall Compiz since I'd like to have the amusing option of turning on wobbly windows and such.  How would I go about doing this?

---

### Post by MyR on 2008-05-23
If you just change your visual effects to none, your settings should be preserved when you reboot.  Is this not the case?

peace

---

### Post by revolutio on 2008-05-23
No, everytime I reboot it goes back to the "Normal" setting.  It would make sense for my settings to be preserved but they are not.

---

### Post by Forlong on 2008-05-23
Running this command (in the terminal) should help:
```
gconftool-2 -s -t string /desktop/gnome/applications/window_manager/default metacity
```

If not, post the output of
```
ls $HOME/.config/autostart
```

---

### Post by revolutio on 2008-05-23
Didn't work, still defaults to Normal after I set it back to None and restart.

Here is the autostart output:
```
beagle-search-autostart.desktop  Pidgin.desktop
bluetooth-applet.desktop         redhat-print-applet.desktop
Compiz Fusion.desktop            Screenlets Daemon.desktop
evolution-alarm-notify.desktop   update-notifier.desktop
gnome-at-session.desktop

```

I may just reinstall all of Compiz since its been pretty pathetic overall since I installed Ubuntu.

---

### Post by Forlong on 2008-05-23
> Compiz Fusion.desktop
That is most probably the root of the problem. Go to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs* and remove anything related to Compiz.

---

### Post by revolutio on 2008-05-26
This covered it, thanks Forlong.

---

