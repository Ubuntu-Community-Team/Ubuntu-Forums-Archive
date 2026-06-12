---
title: "totem-xine"
date: 2005-05-26
forum: General Help
---

### Post by Shakie on 2005-05-26
After reading some reviews and stuff, I hear that totem-xine is the app to use.

I can't find it in Synaptic and apt-get won't grab it. So what I tried to do is install xine and then the totem front end. 

I got xine installed... I think, but I can't get totem installed. Here is the error I get: 

checking for glib-2.0 >= 2.6.3 gtk+-2.0 >= 2.5.6 libgnomeui-2.0 >= 2.3.3 libglad e-2.0 gnome-vfs-2.0 >= 2.1.6 gnome-vfs-module-2.0 >= 2.1.6 gnome-desktop-2.0 >= 2.1.5 iso-codes libmusicbrainz libxine >= 1.0.0 gconf-2.0... Package glib-2.0 wa s not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

configure: error: Library requirements (glib-2.0 >= 2.6.3 gtk+-2.0 >= 2.5.6 libg nomeui-2.0 >= 2.3.3 libglade-2.0 gnome-vfs-2.0 >= 2.1.6 gnome-vfs-module-2.0 >= 2.1.6 gnome-desktop-2.0 >= 2.1.5 iso-codes libmusicbrainz libxine >= 1.0.0 gconf -2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if yo ur libraries are in a nonstandard prefix so pkg-config can find them.

Now I take it that that means I am missing some library requirements, i.e. glib-2.0. However, I can't find that in Synaptic or apt-get either. 

Idea's?

---

### Post by MrTom on 2005-05-26
in synaptic which repositories do you have enabled?

totem-xine is in the 'universe' repository. Here is a guide on enabling universe:
[http://www.ubuntulinux.org/wiki/UniversePackages](http://www.ubuntulinux.org/wiki/UniversePackages)

---

### Post by DutchLau on 2005-05-26
Hello,

Yes indeed, you must enable the "Universe" for Synaptic (apt-get). You do it like [this.](http://ubuntuguide.org/#extrarepositories) 

Then afterwards go to Synaptic and you will find it!  :razz: 

Good Luck!

---

### Post by Shakie on 2005-05-26
Thanks. It was setup a little different in my synaptic for some reason, but with enough looking around, I did enable universe. Thanks a lot.



[edit] And got totem-xine working. [/edit]

---

