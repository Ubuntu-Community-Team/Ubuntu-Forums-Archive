---
title: "[Openbox] What handles the theme of this window?"
date: 2022-06-11
forum: General Help
---

### Post by schwim-dandy on 2022-06-11
Hello there, neighbors!

I've installed Openbox on an Ubu 22.04 server install.  It's not being used as a server, I just needed a min-like install to work off of.  It's my desktop.

I've looked in Obconf, xfce4-appearance and lxappearance but I can't seem to figure this out.  I need the actual window(the part showing the folders and nav pane) to change to a dark theme but I can't seem to figure out what handles that.  What do I need to use to modify the actual window theme(bg color, specifically)?

[COLOR=unset][IMG]https://i.imgur.com/fKvI2UA.png?1[/IMG][/COLOR]
[COLOR=unset][/COLOR]

---

### Post by MAFoElffen on 2022-06-11
OpenBox uses system wide themes, with overrides from User themes. 
> 
Openbox themes are stored in one of the following places: System-wide themes are installed in **/usr/share/themes** . User-specific themes can be installed in ~/. local/share/themes.

Reference: [http://openbox.org/wiki/Help:Themes](http://openbox.org/wiki/Help:Themes)

OpenBox GUI for changing things is ObConf, or manually editing the XML files.

---

### Post by schwim-dandy on 2022-06-11
> **MAFoElffen said:**
> OpenBox uses system wide themes, with overrides from User themes. 

Reference: [http://openbox.org/wiki/Help:Themes](http://openbox.org/wiki/Help:Themes)

OpenBox GUI for changing things is ObConf, or manually editing the XML files.

Thank you for your help but the obconf theme section seems to only deal with titlebar, menu, etc. and not the white body of any of the gui windows.  I need to change the white portion, not the titlebar, menu, etc.

---

### Post by #&amp;thj^% on 2022-06-11
wouldn't this be easier: [https://www.box-look.org/p/1416095/](https://www.box-look.org/p/1416095/)

---

### Post by ajgreeny on 2022-06-11
This tutorial may be useful as well.
[https://ubuntuforums.org/showthread.php?t=2474218](https://ubuntuforums.org/showthread.php?t=2474218)

---

### Post by schwim-dandy on 2022-06-11
> **1fallen said:**
> wouldn't this be easier: [https://www.box-look.org/p/1416095/](https://www.box-look.org/p/1416095/)

The result remains white window bodies:

[IMG]https://i.imgur.com/b9RWXPM.png[/IMG]

---

### Post by schwim-dandy on 2022-06-11
> **ajgreeny said:**
> This tutorial may be useful as well.
[https://ubuntuforums.org/showthread.php?t=2474218](https://ubuntuforums.org/showthread.php?t=2474218)

Thanks very much, I've been using that with a couple other tutorials to help guide me through install list with the goal up ending up with a fully fleshed environment.

---

### Post by Irihapeti on 2022-06-11
The WM looks like PCManFM, which it seems has difficulties with dark themes. See [https://bbs.archlinux.org/viewtopic.php?id=224449](https://bbs.archlinux.org/viewtopic.php?id=224449) PCManFM-gtk3 doesn't appear to be in the Ubuntu repos, so I'm not sure what one could do instead.

(If you're not using PCManFM, ignore what I said.)

---

### Post by schwim-dandy on 2022-06-11
> **Irihapeti said:**
> (If you're not using PCManFM, ignore what I said.)


This is just Thunar FM in OB.  The same packages in my Debian based install look like so, I just can't figure out what was used to create that dark theme:

[IMG]https://imgur.com/X8yFiuEl.png[/IMG]

---

### Post by schwim-dandy on 2022-06-11
Well, it seems that lxappearance handles that look and they call the element "widgets"

[IMG]https://i.imgur.com/DvO37gl.png[/IMG]

---

### Post by MAFoElffen on 2022-06-12
Hmmmm... 'lxappearance' is a GUI Theme Editor, to edit whatever theme you might be using... Something that users would need to install, to be able to use. It was originally created to edit LXDE themes. LXDE uses OpenBox. So yes, that would work.

OpenBox can use LXDE and Gnome thems, which include the GTK+ Toolkit...

Most themes use CSS files, were that setting is in those... But also to change directly in GTK+ as global, you can use dconf-editor and navigate to org.gnome.desktop.interface.gtk-color-scheme... Unselect "use default value", and specify your color choice in hex format...

---

### Post by schwim-dandy on 2022-06-12
> **MAFoElffen said:**
> Hmmmm... 'lxappearance' is a GUI Theme Editor, to edit whatever theme you might be using... Something that users would need to install, to be able to use. It was originally created to edit LXDE themes. LXDE uses OpenBox. So yes, that would work.

I am able to use it to switch pre-installed themes but to edit any elements of them, I have to enable lxsessions, which I don't use.  I'd need to get my hands dirty in the files if I wanted to modify installed themes, I think.

> **MAFoElffen said:**
>  ... you can use dconf-editor and navigate to org.gnome.desktop.interface.gtk-color-scheme... Unselect "use default value", and specify your color choice in hex format...

I'm going to have to look more into that tool as I've never used it.  It looks like a huge settings manager so I wonder how much would play nicely with my oddball patchwork OS install.

Thank you very much for your help and insight, it's really appreciated.

---

### Post by Holger_Gehrke on 2022-06-12
The appearance of applications is mostly governed by settings which are interpreted by the libraries used by the apps. There are two major frameworks - GTK and QT - and dozens of smaller ones ... If an app looks totally different than you expect then it might be using one of those. For GTK 3 based programs you can select themes by setting a 'gtk-theme-name' option in ~/.config/gtk-3.0/settings.ini. There's something similar for programs using GTK 2 in some file in ~/.config/gtk-2.0/. AFAIK settings in those files override setting stored in dconf / gsetting. 

The themes themselves are stored in directories inside /usr/share/themes (systemwide) or ~/.themes (user specific, old) and ~/.local/share/themes (user specific, new). They are made up of .css files but with tag-names and classes that are specific to styling a program instead of a web page. Some themes bundle their assets into files with the extension .gresource, you can list and extract those with the program 'gresource'. 

QT has similar mechanisms and I believe - but don't know since I use very view QT apps - there is a certain degree of compatibility.

Holger

---

### Post by schwim-dandy on 2022-06-13
> **friendlydiamonds said:**
> There are several themes which can be used here , but you need to tell first its older version or newer

Everything is based of a fresh 22.04 install, so my packages are latest currently available in the repos.

---

### Post by schwim-dandy on 2022-06-13
> **Holger_Gehrke said:**
> The appearance of applications is mostly governed by settings which are interpreted by the libraries used by the apps. There are two major frameworks - GTK and QT - and dozens of smaller ones ... If an app looks totally different than you expect then it might be using one of those. For GTK 3 based programs you can select themes by setting a 'gtk-theme-name' option in ~/.config/gtk-3.0/settings.ini. There's something similar for programs using GTK 2 in some file in ~/.config/gtk-2.0/. AFAIK settings in those files override setting stored in dconf / gsetting. 

The themes themselves are stored in directories inside /usr/share/themes (systemwide) or ~/.themes (user specific, old) and ~/.local/share/themes (user specific, new). They are made up of .css files but with tag-names and classes that are specific to styling a program instead of a web page. Some themes bundle their assets into files with the extension .gresource, you can list and extract those with the program 'gresource'. 

QT has similar mechanisms and I believe - but don't know since I use very view QT apps - there is a certain degree of compatibility.

Holger

I've still not manage to figure out what's keeping the themes I've installed in ~/.local/share/themes from actually changing the theme on my install.  They are listed as GTK3/OB themes but I grabbed one off of DeviantArt and another from a Debian install so perhaps they just aren't compatible.  I've tried to keep from bringing in the QT system so I think I'm clear of that added complexity.

This is all a learning process so I don't know the ins and outs of all of the theming but have been aware for some time of the incredibly fractured nature of the look of a simple OB install.

---

