---
title: "Anyone using Gbrowser file manager?"
date: 2006-10-26
forum: General Help
---

### Post by H.E. Pennypacker on 2006-10-26
NOTE: THIS HAS NOTHING TO DO WITH GOOGLE, OR A POSSIBLE BROWSER NAMED GBROWSER.

Is anyone using [GBrowser]("http://gnomefiles.org/app.php/GBrowser"), the file manager?  If so, how'd you get it to work?

There are currently dependency problems with Dapper, and I was wondering if someone found a way to get around them.

---

### Post by Rui Pais on 2006-10-26
hi, 
here builded normally. 
Here the output, check the dependencies 
(libexif and vte at least are needed, the others should exist by default but not sure):
> sudo scons install
scons: Reading SConscript files ...
Checking for gtk+-2.0 >= 2.6.2... ok
Checking for gtk+-2.0 >= 2.8.1... ok
Checking for libexif >= 0.5... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for vte >= 0.11... ok
Checking for libcurl >= 7.13... ok
scons: done reading SConscript files.
scons: Building targets ...
Install file: "gbrowser" as "/usr/local/bin/gbrowser"
Install file: "AUTHORS" as "/usr/local/share/gbrowser/AUTHORS"
Install file: "ChangeLog" as "/usr/local/share/gbrowser/ChangeLog"
Install file: "NEWS" as "/usr/local/share/gbrowser/NEWS"
Install file: "README" as "/usr/local/share/gbrowser/README"
Install file: "TODO" as "/usr/local/share/gbrowser/TODO"
Install file: "glade/download_dialog.glade" as "/usr/local/share/gbrowser/glade/download_dialog.glade"
Install file: "glade/fileinfo.glade" as "/usr/local/share/gbrowser/glade/fileinfo.glade"
Install file: "glade/imageview.glade" as "/usr/local/share/gbrowser/glade/imageview.glade"
Install file: "glade/mainwindow.glade" as "/usr/local/share/gbrowser/glade/mainwindow.glade"
Install file: "glade/settings.glade" as "/usr/local/share/gbrowser/glade/settings.glade"
scons: done building targets.


It's fast, but limited.
PCmanFM do it at least the same and as lighter as gbrowser but it's more mature there is debs available.

---

### Post by H.E. Pennypacker on 2006-10-29
I seem to have everything except:

a@aktop:~/gbrowser-0.4.0$ sudo scons install
scons: Reading SConscript files ...
Checking for gtk+-2.0 >= 2.6.2... no
Cannot find gtk+2-0. Version 2.6.2 or later is required

I searched Synaptic for "gtk+-2.0," "gtk+-," "gtk+2," and "gtk+-2."  Nothing shows up.  I just can't find anything by this name.  What's going on?

I am using Edgy on this computer, but I also have a Dapper laptop.  Why do you have this dependency, but I don't?

---

### Post by Rui Pais on 2006-10-30
> 
Checking for gtk+-2.0 >= 2.6.2... no
Cannot find gtk+2-0. Version 2.6.2 or later is required

I searched Synaptic for "gtk+-2.0," "gtk+-," "gtk+2," and "gtk+-2."  Nothing shows up.  I just can't find anything by this name.  What's going on?

That's one of most misleading error message.
What it needs is a -dev package related with gtk+-2.0 , not the gtk+-2.0 package.

make a search for libgtk2.0-dev and libglib2.0-dev.

(i'm not in edgy right now and in a hurry... can give more details later)

---

