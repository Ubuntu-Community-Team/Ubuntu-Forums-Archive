---
title: "Custom GDM Entry for VMware"
date: 2007-02-23
forum: General Help
---

### Post by blackbeastofaarrgh on 2007-02-23
Hello all,

I remember awhile back that I stumbled upon a tutorial (I don't remember if it was here or not) that gave instructions on how to add a custom GDM entry for VMWare.
Like, instead of starting into GNOME like usual, it would load directly into VMWare. No window manager or anything, just Xorg and VMware.

A few months later, and a fresh installation of Linux, I've forgotten how I did that. Would any of you happen to know how to make an application-specific GDM entry?

---

### Post by DagMan on 2007-02-24
This might help, maybe not.
There are instructions for making beryl startup as a selection in GDM.  If you can work out what you need to run what you're talking about then substituting it should work.  It's a place to start if you can't find the previous page you're looking for.  In the 'configuring beryl' part.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl)
create the file /usr/share/xsessions/Name-Of-Session.desktop
and add the contents as follows
```
[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/File-that-will-be-run-from-gdm
Icon=
Type=Application
```
Filling in the Exec=line with what you need and as you can see, as an example, in the link to beryl, /usr/bin/File-that-will-be-run-from-gdm is a shell script that was also made by the user and had just a couple of commands to run.

Hope that helps.

---

### Post by blackbeastofaarrgh on 2007-02-24
Thanks! Worked perfectly. :D

---

