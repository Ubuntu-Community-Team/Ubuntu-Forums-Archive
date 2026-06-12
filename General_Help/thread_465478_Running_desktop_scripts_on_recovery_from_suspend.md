---
title: "Running desktop scripts on recovery from suspend"
date: 2007-06-05
forum: General Help
---

### Post by ngolian on 2007-06-05
Is there a way to get the Gnome desktop to run a script when recovering from suspend? I know you can add scripts to /etc/acpi/resume.d or whatever, but they don't run in the desktop environment. I use evrouter to make the Windows button act as middle click on my desktop, but for some reason it gets killed when suspended so I need a way to restore it. Some people in the network manager password thread may also find this useful to unlock the keyring again.

---

### Post by Didjit on 2007-06-06
look at "apt-get hibernate" Mostly used for Suspend2, but it has a lot of other features. One which is scriptlets, that will allow you to execute scripts on events. gnome-power-manager will call hibernate, so its already integrated.

Didjit

---

### Post by ngolian on 2007-06-15
hibernate's scriplets just do the same sort of thing as the scripts in /etc/acpi.d don't they? I can't see any way to get it to run a script in my desktop environment.

---

### Post by ngolian on 2007-06-15
I've written a set of scripts to deal with this which I've called [Reveille]("http://www.realh.ukfsn.org/unix/reveille-0.1.tar.gz").

If you're reading this some time after I posted it I may have changed the version number, so check the [directory]("http://www.realh.ukfsn.org/unix/") for newer versions if the first link doesn't work.

---

### Post by arbrandes on 2007-12-27
This Reveille is pretty neat!  Thanks ngolian!

---

