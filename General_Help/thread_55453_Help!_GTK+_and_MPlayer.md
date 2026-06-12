---
title: "Help! GTK+ and MPlayer"
date: 2005-08-09
forum: General Help
---

### Post by demonstenes on 2005-08-09
Hi ! I am a newbie and I need help.
First of all, is there any easy way to install GTK+ ? When I downloaded and unpacked it and tried do ./configure it I got this error:

[I]Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.5.2-head) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.[/I] 

What should I do ? Do I have to install glib, atk, pango and cairo manually ?

Next problem is with MPlayer. I followed steps described at [http://ubuntuguide.org/](http://ubuntuguide.org/) but when I try to play mocie (divx) then the messeage is shown :

*Mplayer interrupted by signal 11 in module: decode audio* 

I' ve got SbLive 5.1. Again - what should I do ?
Cheers !!

---

### Post by Perfect Storm on 2005-08-09
sudo apt-get install libglib2.0-0
sudo apt-get install libglib2.0-dev

Why not getting mplayer from the package manager? (.deb packages)?

---

### Post by demonstenes on 2005-08-09
The main problem is that I need GTK+ in order to install comunicator called Tllenx... The MPlayer is now working  :) 
Cheers !

---

