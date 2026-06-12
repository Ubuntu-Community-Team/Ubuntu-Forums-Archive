---
title: "Glib problems"
date: 2005-06-27
forum: General Help
---

### Post by DavidGX on 2005-06-27
I'm a linux n00b and am having migraine-inducing problems with glib.

(and yes I know gnome comes with xchat I want the newest version)

After trying to install xchat 2.4.4 I got an error message saying I needed glib.. ok.. I found glib and installed that... said I needed GTK or whatever it's called.. fine.. found that and installed it. Installed glib. Got to the ./configure part of xchat 2.4.4 and I'm getting this..

*** 'pkg-config --modversion glib-2.0' returned 2.0.3, but GLIB (2.6.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

I've tried editing LD_LIBRARY_PATH and PKG_CONFIG_PATH to no avail. (Probably because I don't know exactly what to set them to -_-)

Anyone have ANY idea whatsoever what I should do before I pull my hair out have a migraine and go back to windows?

---

### Post by doclivingston on 2005-06-28
What it's reporting is that the glib development libraries are at version 2.0.3, whereas  glib is at version 2.6.3.

Did you install "libglib2.0-dev" with synaptic/apt-get, or did you install the development libraries via some other method? On my (hoary) machine `pkg-config --modversion glib-2.0` return 2.6.3, which it what it should report.

---

