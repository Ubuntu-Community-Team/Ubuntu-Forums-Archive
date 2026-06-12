---
title: "Installing my programs"
date: 2015-02-03
forum: General Help
---

### Post by pauls2 on 2015-02-03
I Have written, compiled and built two programs that I would like to be able to use easily from the desktop. I have information (dated) on making a .desktop file but I need to know where I can safely put my executables so they don't become victims to updates or cleaning that Ubuntu does. Two machines are running Ubuntu 14.04 64 bit and a third machine is running 32 bit Lubuntu 14.04.

where is a safe place to install my software and is there an easier way to copy them and build the .desktop files?

What file types can be used for icons?

Thanks,
Paul

---

### Post by Holger_Gehrke on 2015-02-04
Generally the hierarchy in '/usr/local' is meant for exactly this purpose. I have a few locally compiled programs that have been there since before I updated to Ubuntu 12.04, so they even survived upgrading.

The current spec for .desktop files can be found at [freedesktop.org]("http://standards.freedesktop.org/desktop-entry-spec/latest/index.html"). Icons can be xpm, png and svg (at least I believe so, since there's lot's of them in /usr/share/icons and /usr/share/pixmaps).

---

### Post by slickymaster on 2015-02-04
**/usr/local **is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr.

Locally installed software must be placed within /usr/local rather than /usr unless it is being installed to replace or upgrade software in /usr.

---

### Post by pauls2 on 2015-02-04
Thank you both for the help. One last question on the desktop files:

This is what I have been using:
   [Desktop Entry] 
version=x.y 
Name=ProgramName 
Comment=This is my comment 
Exec=/home/alex/Documents/exec.sh 
Icon=/home/alex/Pictures/icon.png 
Terminal=false 
Type=Application 
Categories=Utility;Application;

and this is what I gathered from freedesktop.org:
[Desktop Entry]
Version=1.0
Type=Application
Name=Foo Viewer
Comment=The best viewer for Foo objects available!
# TryExec=fooview
Exec=fooview %F
Icon=fooview
# MimeType=image/x-foo;
# Actions=Gallery;Create;

[Desktop Action Gallery]
Exec=fooview --gallery
Name=Browse Gallery

[Desktop Action Create]
Exec=fooview --create-new
Name=Create a new Foo!
Icon=fooview-new

In the [Desktop Entry] I have commented out a couple of things that I don't believe I need. Am I wrong?
I also don't believe I need the other two header sections below [desktop entry] so I can leave them out - correct?

Paul

---

