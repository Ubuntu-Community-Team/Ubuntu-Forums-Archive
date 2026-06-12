---
title: "No audio output from VLC"
date: 2005-08-06
forum: General Help
---

### Post by cnayak on 2005-08-06
I downloaded VLC for Gtk+ using apt-get.Everything works fine except there's no sound while playing any format. Any suggestions to fix it?

---

### Post by vvlist on 2005-08-06
Try installing some VLC audio codecs via synaptic. Search for 'VLC,' and there should be  a few '-alsa' or similar. Check it out.

---

### Post by jdodson on 2005-08-06
[QUOTE=cnayak]I downloaded VLC for Gtk+ using apt-get.Everything works fine except there's no sound while playing any format. Any suggestions to fix it?[/QUOTE]

yeah try installing "vlc-esd" that seemed to work on a laptop I owned.

---

### Post by Layden on 2005-08-06
I've encountered this problem on a friend's PC.  Try disabling the Gnome menu/system sounds.  Go to System > Preferences > Sound and then disable everything.

---

### Post by varunus on 2005-08-06
Don't disable ESD...make it work with ALSA!  Follow the configure sound properly howto at the Ubuntu Guide, it lets almost all programs work with sound (if you want a howto with explanations too, that's over in the Tips and Tricks section):
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

I highly recommend NOT turning off GNOME system sounds or the sound server.  If you follow that howto properly, everything will make sound and be happy.

---

### Post by cnayak on 2005-08-06
[QUOTE=varunus]Don't disable ESD...make it work with ALSA!  Follow the configure sound properly howto at the Ubuntu Guide, it lets almost all programs work with sound (if you want a howto with explanations too, that's over in the Tips and Tricks section):
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

I highly recommend NOT turning off GNOME system sounds or the sound server.  If you follow that howto properly, everything will make sound and be happy.[/QUOTE]

  Hey , that works! thanks a lot.

---

