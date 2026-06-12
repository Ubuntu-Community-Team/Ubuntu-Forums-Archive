---
title: "indicator-applet style ..  toolbar icons have no colours"
date: 2013-01-13
forum: General Help
---

### Post by dragonfly41 on 2013-01-13
I have Ubuntu 12.04 LTS 32 bit running in classic mode.

In the top toolbar the icons in indicator-applet (email, network manager, clock etc.) are all grey against black background. No colours seen in icons.

As I add other apps buttons (Tomboy, Dropbox, Ubuntu One) I would like to see some colour in these grey/black toolbar icons.

Launchers placed on the top bar *do* show colours in their icons.

Things I've tried ..

[LIST]
[*]I've looked in Ubuntu Tweak .. but I can't see where to tweak these toolbar button styles.
[/LIST]

[LIST]
[*]Indicator Applet 0.5.0 website .. [http://launchpad.net/indicator-applet](http://launchpad.net/indicator-applet)
[/LIST]

[LIST]
[*]I've looked through FAQ's here ..  [https://answers.launchpad.net/ubuntu/+source/indicator-applet](https://answers.launchpad.net/ubuntu/+source/indicator-applet)
[/LIST]

[LIST]
[*]and I've tried looking at the options in gconftool e.g. --get-schema-name
[/LIST]

---

### Post by 3rdalbum on 2013-01-13
There's not anything inherent in the panel or the indicators that makes the icons grey; it's actually just part of the default Ubuntu icon style.

Load a new set of icons into Gnome (the gnome-look.org website will help you find some, and Gnome Tweak Tool will help you enable one) and they'll appear as intended. Colourful, if that's how they appear in the icon theme.

---

### Post by Frogs Hair on 2013-01-13
Awoken and Acyl are token style icons sets that allow color customization for all icons not just a few selected.  The other option is to change the icons in usr/share/icons/set-name.

The folder location within in the set and method will vary depending on the icon set. I have changed icons in various icon sets but never just the indicators nor with the Ubuntu default icon sets.

---

### Post by dragonfly41 on 2013-01-13
Thanks for the pointers to icon locations ..

In fact I later found this ..

[http://it-connects.co/step-9-change-the-mono-color-icons-on-the-indicator-applet-of-gnome-3-on-ubuntu-12-04-to-color-icons/](http://it-connects.co/step-9-change-the-mono-color-icons-on-the-indicator-applet-of-gnome-3-on-ubuntu-12-04-to-color-icons/)

*[COLOR=DarkRed]Step 9: Change the mono color icons on the indicator applet of gnome 3 on ubuntu 12.04 to color icons[/COLOR]*

Applications > System Tools > Preferences > Advanced Settings > Theme > 

changed Icon theme 

from Ubuntu-mono-dark
to Gnome (default) .. or other theme of your choice

...

Here is another example found ..

[http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/](http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/)

...

---

