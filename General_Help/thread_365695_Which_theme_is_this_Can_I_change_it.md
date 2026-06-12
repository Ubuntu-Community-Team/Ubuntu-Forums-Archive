---
title: "Which theme is this? Can I change it?"
date: 2007-02-19
forum: General Help
---

### Post by ardchoille42 on 2007-02-19
When using gnome I noticed that the gnome-settings-daemon is running to provide your widgets with the theme specified in the gnome-theme-manager. I recently used Window Maker (without gnome-settings-daemon running) and noticed the theme which is used. It's not a bad theme, but I wonder. Where is that theme located? Can I change the colours of that theme? It seems to be the same theme that is running at the gdm login screen - which makes sense since the settings daemon isn't running. How can I change that theme?

---

### Post by tbroderick on 2007-02-20
Download themes in unpack in /home/username/.themes. There is a program called gtk-theme-switch which is a GUI to change gtk themes outside of GNOME. Just run switch2.

---

### Post by ardchoille42 on 2007-02-20
> **tbroderick said:**
> Download themes in unpack in /home/username/.themes. There is a program called gtk-theme-switch which is a GUI to change gtk themes outside of GNOME. Just run switch2.

I'm not sure you understood my question. The theme switch utilities you mentioned are for GTK1 and GTK2 themes in gnome when gnome-settings-daemon is running. When that daemon isn't running, all themes in ~/.themes and /usr/share/themes are ignored.

Have a look at the attached screenshot. This screenshot is in Openbox, so gnome-settings-daemon isn't running. You can see that gtk-theme-switch (the window at the top) is using the Clearlooks-Marble GTK1 theme,  but nautilus (the window below it) isn't using the GTK1 theme. This is because neither GTK1 nor GTK2 themes are used when gnome-settings-daemon isn't running.

I need to know the theme that is being used when gnome-settings-daemon **isn't** running, such as the theme used in the gdm screen when you click Options -> Select Session. That is a widget set that is using a certain theme. This is the theme I want to get hold of and change. gtk-theme-switch doesn't change this theme.

How do I do that?

---

### Post by tbroderick on 2007-02-20
Changing gtk1 theme will do nothing to nautlus or most GNOME apps including GDM. You need to change gtk2 theme by running switch2 not switch. GDM has it's own theme manager. You can run sudo gdmsetup. You can change the the GDM theme or the gtk2 theme that GDM uses.

---

### Post by ardchoille42 on 2007-02-20
Ok, here's what I found out. 

1) The theme that is used in GTK2 apps when gnome-settings-daemon is not running.. this is not a theme. This is pure unthemed GTK2. When I used switch2 to change the GTK2 theme, while gnome-settings-daemon **wasn't** running, there was no change in the themes of GTK2 apps.

2) You can change the GTK1 theme that is used at the gdm screen. I have included an email which explains how to do this. I have tried this on Ubuntu 6.06.1 LTS and it works fine. Here is the email:

```

Re: GTK theme for thegreeter screen?
from [Brian Cameron]
To: 	seb128@debian.org, gdm-list@gnome.org
Subject: 	Re: GTK theme for thegreeter screen?
From: 	Brian Cameron <Brian.Cameron@Sun.COM>
Date: 	Tue, 21 Feb 2006 14:21:21 -0800

Sebastien Bacher said:

> gdm.conf has that comment:
> "# If to allow changing the GTK+ (widget) theme from the greeter.
> Currently
> # this only affects the standard greeter as the graphical greeter does
> not yet
> # have this ability."
>
> Is there any technically reason that applying a theme works for the
> standard banner but not the greeter one? Do you have any idea of what
> change would be required for that?

I just added a change to GDM that allows a gdmgreeter theme to specify
a GTK theme to be used.

All you have to do is use GDM from CVS head, and use this syntax in
your gdmgreeter theme:

<greeter gtk-theme="ThemeName">

instead of just <greeter>

I think this does what you are looking for.

Also, you suggested you were going to improve the Options menu so the
menu pops below the button if there is enough room.  Any progress on
this patch?  It'd be nice to get this in before 2.14 release.

Thanks!

Brian
_______________________________________________
gdm-list mailing list
gdm-list@gnome.org
http://mail.gnome.org/mailman/listinfo/gdm-list

```

I did not see anything in gdmsetup that allows the user to change the GTK theme used in the dialogs in GDM.

---

### Post by tbroderick on 2007-02-20
When you ran switch2 were there themes there? Did it create a ~/.gtkrc-2.0?

---

