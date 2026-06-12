---
title: "Xfce and wine"
date: 2006-10-19
forum: General Help
---

### Post by Drezliok on 2006-10-19
I'm using XFce and the menu it made for my wine programs is cluttered. I can't edit them out.

I'm totally confused. I've looked at the help files and can't figure out how to get into the menu to edit it.

> 
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<title name="Desktop Menu" icon="xfce4-backdrop"/>
	<separator/>
	<app name="Run Program..." cmd="xfrun4" icon="gnome-fs-executable"/>
	<separator/>
	<app name="Terminal" cmd="xfterm4" icon="gnome-terminal"/>
	<app name="File Manager (thunar)" cmd="thunar" icon="Thunar"/>
	<app name="Web Browser" cmd="/usr/bin/firefox" icon="/usr/share/firefox/icons/default.xpm"/>
	<separator/>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	**<include type="system" style="simple"/>**
	<separator/>
	<app name="Help" cmd="xfhelp4" icon="gnome-help"/>
	<app name="About Xfce" cmd="xfce4-about" icon="gnome-info"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>



The part thats bolded is where the clutter is at and I want to get the dead progs out of the menu

Thankyou for your time.
Drezliok

---

### Post by liniaal on 2008-01-31
I have a similar problem i think.. in the xfce menu (i installed the xfce4 package over a normal ubuntu installation, because i like the xfce panel more) the wine 'programs' folder doesn't even show up! is this a known bug?
It does seem to place the shortcuts, that should be in the wine submenu, under "other". But it can't find the icons. With this i'll add a vim screenshot;

[IMG]http://liniaal.doesntexist.org/sjiekesjit/gvim-googlesketchup-desktop.png[/IMG]
as find found 2 (apparently, remarkably different!) versions of googlesketchup.desktop.

---

