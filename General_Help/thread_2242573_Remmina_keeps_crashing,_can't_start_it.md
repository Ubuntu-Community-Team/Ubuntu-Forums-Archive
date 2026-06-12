---
title: "Remmina keeps crashing, can't start it"
date: 2014-09-02
forum: General Help
---

### Post by z0rr099 on 2014-09-02
Just installed Remmina on my Kubuntu 14.04, fully updated system. When I run it from a terminal, I get the following:

eff@linuxbox:~$ remmina
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.

(remmina:3082): Gtk-CRITICAL **: gtk_tree_model_filter_get_value: assertion 'GTK_TREE_MODEL_FILTER (model)->priv->stamp == iter->stamp' failed

(remmina:3082): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.0/./gobject/gtype.c:4210: type id '0' is invalid

(remmina:3082): GLib-GObject-WARNING **: can't peek value table for type '<invalid>' which is not currently referenced
Segmentation fault (core dumped)
-----------------------------------------------

System information:

jeff@linuxbox:~$ lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:cxx-4.1-ia32:cxx-4.1-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:desktop-4.1-ia32:desktop-4.1-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:graphics-4.1-ia32:graphics-4.1-noarch:languages-3.2-ia32:languages-3.2-noarch:languages-4.0-ia32:languages-4.0-noarch:languages-4.1-ia32:languages-4.1-noarch:multimedia-3.2-ia32:multimedia-3.2-noarch:multimedia-4.0-ia32:multimedia-4.0-noarch:multimedia-4.1-ia32:multimedia-4.1-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:printing-4.1-ia32:printing-4.1-noarch:qt4-3.1-ia32:qt4-3.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

---

