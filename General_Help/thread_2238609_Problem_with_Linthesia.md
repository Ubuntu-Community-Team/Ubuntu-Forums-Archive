---
title: "Problem with Linthesia"
date: 2014-08-08
forum: General Help
---

### Post by Santiago_Freire on 2014-08-08
Hi,
I was trying to run Linthesia in my Ubuntu 14.04 AMD64 machine, and when I put it in the terminal, it gives the following error:
> Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

(linthesia:30844): GdkGLExt-WARNING **: cannot load PangoFont

(linthesia:30844): glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: std::exception

«trap» para punto de parada/seguimiento (`core' generado)


Sorry for my english :grin:
I appreciate your help :wink:

---

### Post by claracc on 2014-08-09
It seems to be a known old bug with this software package: see [https://bugs.launchpad.net/ubuntu/+source/linthesia/+bug/663962/](https://bugs.launchpad.net/ubuntu/+source/linthesia/+bug/663962/)

See all the comments, the problem is related to some kind of font letter ( pango one) not installed in the system. In the same link are workarounds and patches which reported as working for certain people.

---

