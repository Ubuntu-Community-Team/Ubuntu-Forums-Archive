---
title: "I can't get &quot;Character Map&quot; in gedit to work"
date: 2021-01-28
forum: General Help
---

### Post by Paddy Landau on 2021-01-28
A rather old answer shows [how to use Character Map in gedit]("https://askubuntu.com/a/484100/2088"). It certainly used to work, as evidenced by a comment that I myself made to the answer.

However, I can no longer get it to work.

When I select "Character Map" in the side pane, I get a list of fonts as expected. But, the list of characters is nowhere to be found! I've attached a screenshot below.

How can I get this to work?

[LIST]
[*]Ubuntu 20.04
[*]gedit 3.36.2 (from the standard repository)
[*]Gnome 3.36.8
[/LIST]

---

### Post by vanadium on 2021-01-28
I can only confirm what you observe, on Ubuntu 20.10. Newer versions of gedit seem to have broken the plugin, although it is still shipped.

---

### Post by Paddy Landau on 2021-01-28
Thank you. I've raised this as a [bug report on gedit]("https://gitlab.gnome.org/GNOME/gedit/-/issues/406"). Please would you give a "thumbs up" to the report.

---

### Post by Paddy Landau on 2021-02-21
A [fix has been applied]("https://gitlab.gnome.org/GNOME/gedit-plugins/-/issues/41"). I don't know how to get the latest gedit, though. There doesn't seem to be a PPA for it.

---

### Post by Holger_Gehrke on 2021-02-21
It's not a new gedit you need, you just need the updated files from the plugin. Download the __init__.py and panel.py and put them in /usr/lib/x86_64-linux-gnu/gedit/plugins/charmap/; you might want to rename the originals before copying the new ones there so you can reverse the change if something else goes wrong. Gedit plugins are written in Python and don't need to be compiled to work.

Or to do it in a cleaner way you can remove the gedit-plugin-charmap package and manually install the plugin into ~/.local/share/gedit/plugins (might have to replace the same two files with the new versions).

Holger

---

