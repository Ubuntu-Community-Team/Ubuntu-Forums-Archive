---
title: "How to properly load nm-applet.desktop?"
date: 2014-06-23
forum: General Help
---

### Post by PeterTaps on 2014-06-23
[COLOR=#000000]Folks,[/COLOR]

[COLOR=#000000]I am running minimal Ubuntu 14.04 + openbox + network-manager.[/COLOR]

[COLOR=#000000]In the past, when I bring up openbox, "ps" would reveal that nm-applet is running (because of /etc/xdg/autostart/nm-applet.desktop). However, there would be no visible icon for me to configure wireless, etc.[/COLOR]

[COLOR=#000000]The following is the workaround I used to use:[/COLOR]

[COLOR=#000000]1. sudo apt-get install docker[/COLOR]
[COLOR=#000000]2. sudo rm /etc/xdg/autostart/nm-applet.desktop[/COLOR]
[COLOR=#000000]3. Edit autostart and add the following two lines[/COLOR]

[COLOR=#000000]docker &[/COLOR]
[COLOR=#000000](sleep 3 && nm-applet) &[/COLOR]

[COLOR=#000000]This ensured that docker runs before nm-applet and the icon becomes visible under docker.[/COLOR]

[COLOR=#000000]However, I would prefer to use /etc/xdg/autostart/nm-applet.desktop, if possible, and not go through this workaround. So, it is possible to perhaps create "docker.desktop" and make nm-applet.desktop dependent on it? Or, is there a better solution?[/COLOR]

[COLOR=#000000]Another related question. So far I have not used any panel with openbox. I am leaning towards lxpanel. I understand lxpanel already has systray and therefore I won't need docker anymore. If I do switch to lxpanel, how can I ensure that lxpanel runs first before nm-applet kicks in?[/COLOR]

[COLOR=#000000]Thank you in advance for your help.[/COLOR]

[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Peter[/COLOR]

---

### Post by Bucky Ball on 2014-06-23
*Thread moved to **General Help**.*

---

### Post by PeterTaps on 2014-06-27
I tried various settings. The closest I got was the following:

Edit nm-applet.desktop so that it runs with dbus-launch.

With this change, it does not matter if nm-applet runs before the systray application (docker/lxpanel). When the systray app comes up, you will see nm-applet icon in your systray.

However, you cannot add/modify entries.

Based on a post, I added my userid to netdev group. This didn't help either.

Bottom line. Don't bother using nm-applet.desktop. Just delete that file and run "sudo nm-applet" via autostart or manually after bringing up openbox window manager.

Regards,
Peter

---

