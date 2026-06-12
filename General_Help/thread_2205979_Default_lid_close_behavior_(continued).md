---
title: "Default lid close behavior (continued)"
date: 2014-02-16
forum: General Help
---

### Post by richardbrucebaxter on 2014-02-16
This thread is requesting a solution to the problem identified here ([http://ubuntuforums.org/showthread.php?t=2017231](http://ubuntuforums.org/showthread.php?t=2017231)).

I was wondering where the settings are to control the default lid close behaviour before logging in (gnome control center power management / dconf-editor settings are not respected). 

This issue is particularly important when using a window manager other than Ubuntu (e.g. icewm), as alternative window managers do not respect the gnome control center power management / dconf-editor settings either. (I imagine an alternative solution might involve executing gnome-power-manager upon icewm startup rather than a mate-power-manager, but Ubuntu 13.1 does not provide a gnome-power-manager executable to try this).

Note I tried creating a gschema.override file in /usr/share/glib-2.0/schemas/ but this had no effect (without documentation it is hard to say whether this is correct);
	[org.gnome.settings-daemon.plugins.power]
	lid-close-ac-action='nothing'
	lid-close-battery-action='nothing'

Cheers,

Richard

---

### Post by richardbrucebaxter on 2014-02-19
I found the solution to this problem [here]("http://askubuntu.com/questions/360615/ubuntu-server-13-10-now-goes-to-sleep-when-closing-laptop-lid");

sudo gedit /etc/systemd/logind.conf

change;
    #HandleLidSwitch=suspend
to;
    HandleLidSwitch=ignore

---

