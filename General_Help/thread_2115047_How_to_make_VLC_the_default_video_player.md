---
title: "How to make VLC the default video player?"
date: 2013-02-11
forum: General Help
---

### Post by rva1945 on 2013-02-11
HI:

when I double-click on a movie file, it is opened with Movie PLayer. I can right-click and select VLC (VideoLAN but it's a pain doing it once and again).

I tried to uninstall Movie Player from the package manager but I get this:

To remove Movie Player, these items must be removed as well:

The gnome desktop envoronment - essential components
gnome-core

Totem mozilla plugin
totem-mozilla

Plugins for the totem media player
totem-plugins

Now will removing those items ruin my Ubuntu 12.04?

thanks

---

### Post by rva1945 on 2013-02-11
ANSWERED: right-click on file, Properties, open with... set default..

Thanks

---

### Post by lovevn on 2013-02-12
> **rva1945 said:**
> HI:

when I double-click on a movie file, it is opened with Movie PLayer. I can right-click and select VLC (VideoLAN but it's a pain doing it once and again).

I tried to uninstall Movie Player from the package manager but I get this:

To remove Movie Player, these items must be removed as well:

The gnome desktop envoronment - essential components
gnome-core

Totem mozilla plugin
totem-mozilla

Plugins for the totem media player
totem-plugins

Now will removing those items ruin my Ubuntu 12.04?

thanks
Hi. You can choose: System Settings -> Details -> Default Applications, then check Video, choose VLC. 

[IMG]http://www.flickr.com/photos/85810852@N02/8467548624/[/IMG]
[IMG]http://www.flickr.com/photos/85810852@N02/8467548624/[/IMG]

[IMG]http://i.upanh.com/voasee[/IMG]

---

### Post by Yellow Pasque on 2013-02-12
And to answer your other question, it is safe to remove totem. The 2 totem- packages are obviously part of totem and gnome-core is just a metapackage that depends on other packages (one of which is totem).

Please mark this thread [SOLVED] (using thread tools menu at the top).

---

