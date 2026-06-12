---
title: "HowTo:  Icon to toggle desktop effects, and manager for effect behavior in 8.04"
date: 2008-04-29
forum: General Help
---

### Post by TokyoYank on 2008-04-29
[B][I]**For 9.04 users, see edit below
[/I][/B]
Many laptop users and users of slower desktops (like me) may have some difficulties when using hardy heron 8.04.  Desktop effects are on by default, but if you don't use an expensive and/or recent graphics card, you could get some blinking or flickering if you install another program that needs 3D graphics (for example fun games such as foobillard or scorched3d).  To increase performance of the application, you can decrease the performance of the desktop.  At the same time, it is easy to add a manager that offers more control over which desktop effects are active than what is afforded via System > Preferences > Appearance

[LIST=1]
[*]System > Administration > **Synaptic Package Manager**.  Search for the keyword *compiz* -- that is the name for the package that controls desktop effects.  This HowTo covers the use of two packages you should add:[LIST]
[*]fusion-icon
[*]compizconfig-settings-manager
[/LIST]This HowTo assumes that after the above packages & dependencies are installed, searching *compiz* shows the following packages with a green tick to indicate they're installed:  *compiz, compizconfig-backend-gconf, compizconfig-settings-manager, compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, compiz-plugins, fusion-icon, libcompizconfig0, libdecoration0, python-compizconfig*
[*]**fusion-icon**[LIST]  --  the easy way to toggle OFF draining effects
[*]Even though the package is installed, it does not appear automatically and must be configured  [LIST]
[*]For now, turn it on manually, Applications > System Tools > Compiz Fusion Icon
[/LIST]
[*]8.04:  System > Preferences > Sessions > Add
9.04:  System > Preferences > Startup Applications > Add
Enter the following:[LIST]
[*]*Name*:  Compiz fusion-icon
[*]*Command*:  fusion-icon
[*]*Comment*:  Panel icon to toggle desktop effects[/LIST]
[*][OK].  If you don't see a blue cube + arrow icon in the upper right corner, log out and log in again.  
[*]**To toggle effects OFF**:  right click the icon > Select Window Manager > **Metacity**.  To toggle them back ON, choose **Compiz**.
[/LIST]
[*]**compizconfig-settings-manager**[LIST]
[*]Left click in the icon installed above and select "Settings Manager".  Alternatively, the same can be reached via System > Preferences > Advanced Desktop Effects Settings
[*]Now you can fine-tune the effects.  I personally want to use a feature which makes it easy to find obscured windows--apparently this effect is similar to a Mac effect called "Expose"
[*]Example:  "**Scale**"[LIST]
[*]Scroll down to find Scale.  Or:  Category > Window Management > Scale
[*]Click on the text of Scale (note:  Click on the text, not the check box).  This accesses the settings for the plugin.
[*]**Bindings**:  this is how the actions within the desktop interact with the plugin
[*]I want to configure the desktop so that when I move the mouse into the upper right corner, it displays my hidden windows using the Scale plugin.  The binding I want is "Initiate Window Picker".
[*]However, you'll notice there are three.  One has a screen icon, another a keyboard, and the last one a mouse.  It's possible to configure screen motion, keyboard shortcuts, and mouse clicks, if you like.  I want to configure a mouse location on the screen, so I click the top button reading [Disabled]
[*]A depiction of the screen with many zones is depicted.  Available zones are denoted in green.  I click in the upper right corner, and the green highlight turns red to indicate that I picked it.
[*]The settings are updated in real-time, so you can try it immediately.
[/LIST]
[/LIST]
[/LIST]

This is my first HowTo (yeah I'm giving something back) so please let me know if something isn't clear. .. or if it's useful!  Cheers


***edit***:  Update for 9.04, some observations on a fresh install:[LIST]
[*]3D effects are not turned on by default.  *(My comment above on 8.04 inaccurate?)*
[*]The above instructions still work, however **you must first**:[LIST]
[*]Install Synaptic Package Manager[LIST=1]
[*](Connect to the internet)
[*]Applications > Accessories > Terminal
[*]sudo apt-get synaptic
[/LIST]
[*]Enable the 3D video card driver[LIST=1]
[*]System > Configuration > Hardware Drivers
[*]... If you don't see a "waiting" bar where it searches for available drivers, you might need to have "Proprietary drivers for devices" enabled, at startup or System > Administration > Software Sources
[*]Select a driver for accelerated graphics.  For my nVidia card, I had three options, with one being recommended.
[/LIST]
[/LIST]
[/LIST]

---

### Post by marlboro05 on 2008-07-06
Just the howto I was looking for!

Thank you

---

### Post by TokyoYank on 2009-08-06
Anyone (admins?) think this should be on a wiki?

"Scale" is listed in the header of the link below, but not discussed:

[https://help.ubuntu.com/9.04/desktop-effects/C/compiz-default-plugins.html#expo](https://help.ubuntu.com/9.04/desktop-effects/C/compiz-default-plugins.html#expo)

---

