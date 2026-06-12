---
title: "Some command line options to manually change appearance in gnome..."
date: 2007-11-27
forum: General Help
---

### Post by darkmaster on 2007-11-27
Hello everyone, maybe this is very easy for you but for me not ;)
Could anyone tell me how to manually change from command line the:
- icon theme
- background
- metacity theme
in gnome, in Feisty?
I need to create script able of customizing these aspects of the desktop, so I can't use the normal graphical tools. Also, is there a way to automatically set an entire theme in gutsy via command line (entire theme I mean a set of background, icons, gtk-theme, etc)? I mean, if I created with the gutsy utilities a complete theme, can I directly switch to that theme using the command line?

For the gtk theme I used gtk-theme-switch, but it only changes the gtk-theme and it does not accept an entire gnome-theme. 

Please, any help?

---

### Post by spupy on 2007-11-27
I haven't heard of a CLI program that can change the theme. One possible solution that comes to mind is to write a simple script that creates the ".gtkrc-2.0" in the home directory.  This file describes the gtk theme, the icon theme and some other properties of the GTK programs. But this file is not used by gnome if the program gnome-settings-daemon is running. Here is an example how my ".gtkrc-2.0" file looks like (i don't use gnome, just gtk):
```
include "/home/uibxn/.themes/Aurora/gtk-2.0/gtkrc"

include "/home/uibxn/.gtkrc.mine"

gtk-toolbar-style = GTK_TOOLBAR_ICONS
gtk-icon-theme-name="Tango"
```

EDIT: Another idea: find a way to edit gconf. This is something like the windows registry, and i think most of the configurations are kept in there (i.e. metacity theme, gtk theme, desktop background). The files are located in ".gconf/" directory in the home folder. The files are written in XML. For example, the configuration file for metacity is located at 
```
~/.gconf/apps/metacity/general/%gconf.xml
```
You can use gconf-editor to find the location of other conf files.

---

### Post by qamelian on 2007-11-27
You can probably set all these items through gconf by using gconftool in you script. You'll need to locate the appropriate keys in gconf and call gconftool to change the settings to those you want.

[http://linux.die.net/man/1/gconftool-2](http://linux.die.net/man/1/gconftool-2)

---

### Post by darkmaster on 2007-11-27
> **qamelian said:**
> You can probably set all these items through gconf by using gconftool in you script. You'll need to locate the appropriate keys in gconf and call gconftool to change the settings to those you want.

[http://linux.die.net/man/1/gconftool-2](http://linux.die.net/man/1/gconftool-2)

OK, this option is probably much more likely. But isn't there a command line option, really? That's weird! What the hell does gnome-theme-manager do after all? And I'm running gnome-settings-daemon, so the first option is not OK ;)

Thank you, any other suggestion?

---

### Post by spupy on 2007-11-27
Well, the gconftool idea that qamelian gave sounds good to me!

---

### Post by darkmaster on 2007-11-27
> **spupy said:**
> Well, the gconftool idea that qamelian gave sounds good to me!

Yeah, well, I experimented it a bit and it does work fine :)
Let's say this post is solved them :D

---

