---
title: "Limited Locked Memory"
date: 2016-10-23
forum: General Help
---

### Post by danimal2 on 2016-10-23
[COLOR=#333333][FONT=&quot]Hey guys, when I start Ardour I get this message:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]"WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to run out of memory before your system runs out of memory."[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I've found one thread about this from 3 years ago on the Ardour forums (and with an older version of Xubuntu) but there was no clear solution, and what I tried didn't help.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I've tried:
sudo -i
ulimit -l unlimited[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Checking the memory afterwards, even after logging out, rebooting, etc. that it doesn't change. They said after entering ulimit -l it should say "unlimited" but it just says "64". Maybe it's locked at 64%? Maybe 64 is the max? It's not clear.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Also added #@audio-memlock unlimited to limits.conf with no results.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Would appreciate some help![/FONT][/COLOR]

---

### Post by T.J. on 2016-10-24
> **danimal2 said:**
> [COLOR=#333333][FONT=&amp]Hey guys, when I start Ardour I get this message:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]"WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to run out of memory before your system runs out of memory."[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I've found one thread about this from 3 years ago on the Ardour forums (and with an older version of Xubuntu) but there was no clear solution, and what I tried didn't help.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I've tried:
sudo -i
ulimit -l unlimited[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Checking the memory afterwards, even after logging out, rebooting, etc. that it doesn't change. They said after entering ulimit -l it should say "unlimited" but it just says "64". Maybe it's locked at 64%? Maybe 64 is the max? It's not clear.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Also added #@audio-memlock unlimited to limits.conf with no results.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Would appreciate some help![/FONT][/COLOR]

You may find some useful information here: [https://wiki.debian.org/Ardour](https://wiki.debian.org/Ardour)

---

### Post by danimal2 on 2016-10-25
> **T.J. said:**
> You may find some useful information here: [https://wiki.debian.org/Ardour](https://wiki.debian.org/Ardour)

Ok so when I enter [COLOR=black]**sudo gedit /etc/pam.d/common-session**, the file opens up but I get a bunch of error messages in my terminal.

They say:
[/COLOR](gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:27:35: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:40:48: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:48:46: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:59:58: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:70:46: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:81:58: Junk at end of value

I added [COLOR=black]**session required pam_limits.so** to the file but once I close it, this message shows up in the terminal:
[/COLOR]** (gedit:3223): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

The added line to common-session saves though...

---

### Post by T.J. on 2016-10-26
> **danimal2 said:**
> Ok so when I enter [COLOR=black]**sudo gedit /etc/pam.d/common-session**, the file opens up but I get a bunch of error messages in my terminal.

They say:
[/COLOR](gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:27:35: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:40:48: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:48:46: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:59:58: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:70:46: Junk at end of value


(gedit:3223): Gtk-WARNING **: Theme parsing error: gtk.css:81:58: Junk at end of value

I added [COLOR=black]**session required pam_limits.so** to the file but once I close it, this message shows up in the terminal:
[/COLOR]** (gedit:3223): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

The added line to common-session saves though...

The warnings are theme errors, quite common these days since the Gnome Project released GTK 3.  GTK 3's interface is quite unstable from version to version.  It's so bad that some theme creators simply quit supporting themes at all because of it - so you will get all kinds of theme errors.  Just ignore it, it's not relevant to what you are trying to do, and in most cases:  other than funny looking windows, it is relatively harmless.  If it bothers you, try switching the theme to Adwaita - the only theme that Gnome officially supports.  The second about document metadata is a known bug in gedit - also from the Gnome Project.  I wouldn't worry too much about warnings as long as the file saves correctly.  Just make sure you backup something before you change it.  IMO, Gnome has gotten very sloppy.  Their programs post warnings all the time these days.  Their management process since moving to Gnome 3 leaves much to be desired.  Still, it's not my project and they can run it as they see fit.  It's just really inconvenient for the rest of us to have to deal with.

I hope Ardour works now?

---

### Post by danimal2 on 2016-11-01
> **T.J. said:**
> I hope Ardour works now?

Well it seems it's been working the whole time, but I've been trying to fix the memory issue before I really start working with it so I can eliminate the problem that seems I'll inevitably run into in the near future. But sadly, I'm *still* getting the message. I had hoped the OS update I installed today would help, but nope. Seems these fixes I've tried works for everyone but me... quite disheartening. I'm certain I'm executing them correctly, but I guess there's something I'm missing...

---

