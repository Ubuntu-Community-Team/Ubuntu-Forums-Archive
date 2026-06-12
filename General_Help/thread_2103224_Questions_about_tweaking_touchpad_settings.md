---
title: "Questions about tweaking touchpad settings"
date: 2013-01-09
forum: General Help
---

### Post by AleveSicofante on 2013-01-09
(I have asked this question at askubuntu.com, but maybe that place is no the proper one, since I'm getting no replies at all.)

Currently there are just too many places to set touchpad properties and behaviour.

1. The default sytem settings mouse and touchpad tool.
2. The dconf-editor key /org/gnome/settings-daemon/plugins/mouse/
3. The synclient tool
4. The syndaemon tool
5. The xinput tool
6. The gpointing-device-settings tool.
7. Editing files inside the /etc/X11/xorg.conf.d/ directory

I wouldn't be surprised if there were even more places...

Now my question is: I want a single place to control the touchpad. Synclient seems to cover all the bases. If that's correct, how can I get rid of EVERYTHING ELSE? Or should I go another route?

Currently syndaemon seems to be run by lightdm, and I can't tell if it's interfering with my synclient settings referring to disabling the touchpad while typing; or not (the fact is I can't get rid of the touchpad interfering with the typing). I also wouldn't know how to stop lightdm from starting an instance of syndaemon if that was the case.

The gpointing-device-settings tool, while nice, seems obsolete and doesn't write the settings anywhere meaningful, so it has to be run each time the system is either woken up from sleep or reboot.
 
It seems the key at dconf-editor must be deactivated in order for X11 to gain control over the touchpad, otherwise there's no way to know who's controlling who (X11 or Gnome). Why are there two instances of controlling the touchpad. Is it better to leave Gnome under control or X11?

There's no way to tell what the default system settings touchpad section does, after using any of the other methods. Is it overriden by synclient, xinput, xorg.conf.d files or viceversa?

Finally, it's unclear if I should use synclient or xinput, which one takes precedence, etc.

tl;dr: Since there are just too many ways to tweak the touchpad settings and some seem to override others, I need a clearer idea of what's the hierarchy, the conflicts and the best way to handle the touchpad. I'm willing to read all the documentation there is about the subject, I just can't seem to find the proper one.

Currently, syndaemon is not doing what's supposed to do and the corresponding synclient parameters aren't either. I'm on a Macbook 1,1 and Ubuntu 12.04.

Thanks.

---

